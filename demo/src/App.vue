<style lang="less">
.v-carousel-item {
	height: 800px;
}
</style>
<template>
	<div>
		<h3>Vue Carousel Example</h3>
		<carousel ref="car" @changed-index="log" :auto="auto" :watch-items="list" :dots="true" :loop="loop" :speed="speed" :rewind="rewind" :mouse-drag="mouseDrag">
			<carousel-item
				v-for="(item, index) in list"
				v-bind:image="item.image"
				v-bind:infoPanel="item.infoPanel"
			></carousel-item>
		</carousel>
	</div>
</template>
<script>
import { Carousel, CarouselItem } from '../../src/index';

var list1 = [
	{
		image: { backgroundImage: 'url(http://via.placeholder.com/350x150)' },
		infoPanel: {
			title: 'Cultivo',
			text: `En las regiones montañosas de Cauca y Nariño, a aproximadamente
			2000 metros de altura, los caficultores cultivan principalmente la
			variedad Castillo del Arábica.  La altura genera sabores finos y una
			acidez intensa del café.  La altura y la sombra (ya sea proveniente de
			los árboles o las nubes) significa que el grano toma más tiempo para
			madurar, y que absorbe todo el azúcar de la fruta que lo rodea.  El Cauca
			es una de las regiones cafeteras con el mayor número de caficultores
			participantes en el Programa de Calidad Sostenible AAA™ de Nespresso.  A
			lo largo de los últimos siete años, hemos trabajado de cerca con socios
			locales como la Federación de Cafeteros y con comunidades de caficultores
			en el Cauca para proteger y regenerar su terroir, al tiempo que
			triplicamos la cantidad de café AAA que producen.  Algunos de estos
			caficultores han participado en nuestro programa de agro-silvicultura
			plantando alrededor de 80.000 árboles nativos; también están ahorrando
			100,000m3 de agua cada año, a través de la aplicación de mejores
			prácticas así como la utilización de sistemas de tratamiento de aguas
			suministrados por Nespresso.`,
			quote: {
				hasQuote: false,
				title: '',
				subtitle: '',
				text: ``,
			},
		},
	},
	{
		image: { backgroundImage: 'url(http://via.placeholder.com/450x150)' },
		infoPanel: {
			title: '',
			text: ``,
			quote: {
				hasQuote: false,
				title: '',
				subtitle: '',
				text: ``,
			},
		},
	},
	{
		image: { backgroundImage: 'url(http://via.placeholder.com/550x150)' },
		infoPanel: {
			title: 'Selección',
			text: `Al final de cada día, los caficultores separan las cerezas a mano,
			para eliminar las verdes.  Debido a que las cerezas no maduras agregan un
			nivel de astringencia desagradable a la taza de café, y por ende reduce
			las ganancias de los caficultores, capacitamos a los caficultores para
			que recojan el mayor número posible de cerezas rojas.`,
			quote: {
				hasQuote: true,
				title: 'Programa de Calidad Sostenible AAA',
				subtitle: 'Definición',
				text: `En 2003, se creó el Programa de Calidad Sostenible AAA de
				Nespresso en asocio con la Rainforest Alliance. Este programa cafetero
				desarrollado específicamente asegura que podamos ofrecerle un café de
				la mejor calidad al tiempo que apoyamos el sustento sostenible de
				agricultores y sus comunidades, protegiendo el medio ambiente.`,
			},
		},
	},
];

export default {
	components: {
		'carousel': Carousel,
		'carousel-item': CarouselItem,
	},
	data() {
		return {
			auto: 0,
			list: list1,
			speed: 300,
			loop: true,
			rewind: false,
			mouseDrag: true,
		};
	},
	mounted() {
		var me = this,
			car = me.$refs.car;
		car.$on('changed-index', function () {
			console.log(arguments);
		});
	},
	methods: {
		toggleAuto() {
			this.auto = this.auto === 0 ? 3000 : 0;
		},
		toggleLoop() {
			this.loop = !this.loop;
		},
		toggleRewind() {
			this.rewind = !this.rewind;
		},
		toggleMouseDrag() {
			this.mouseDrag = !this.mouseDrag;
		},
		log(content) {
			console.log(content);
		},
		to(e) {
			this.$refs.car.$emit('to', e.target.value);
		},
		indexChanged(index, total, item) {
			var me = this,
				log = me.log;
			log('Slide end:' + index);
			log(item);
		},
		changeList() {
			this.list = this.list == list1 ? list2 : list1;
		},
	},
};
</script>
