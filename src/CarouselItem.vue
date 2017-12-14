<style lang="less">
div#app .v-carousel {
	&-item {
		width: 100%;
		float: left;
		display: flex;
		height: 950px;
	}
	&-item > div:first-of-type {
		flex: 2;
		max-width: 100%;
		background-position: center;
		background-size: cover;
	}
	&-item > div:last-of-type {
		flex: 1;
		background-color: #27221f;
		color: #fff;
		font-family: 'Open Sans';
		padding: 2rem;
		overflow-y: overlay;
		& > h3 {
			color: inherit;
			font-size: 1.28571rem;
			line-height: 1.33333;
			letter-spacing: 0.26667rem;
			font-weight: 800;
			text-transform: uppercase;
			padding-bottom: 1rem;
		}
		& > p {
			color: inherit;
			font-size: 1rem;
			line-height: 1.44444;
			letter-spacing: 0.05556rem;
			font-weight: 300;
		}
		& > div {
			position: relative;
			padding-left: 1.5rem;
			&:before {
				content: "";
				height: 100%;
				width: 0.3rem;
				background: rgba(0, 0, 0, 0.15);
				position: absolute;
				top: 0;
				left: 0;
				background-color: #fff;
			}
			& > h4 {
				font-size: 1.2rem;
				margin: 0 0 1rem;
				color: inherit;
			}
			& > h5 {
				margin: 0 0 1rem;
				text-transform: uppercase;
				font-weight: 500;
				letter-spacing: .14286em;
				color: inherit;
			}
			& > p {
				line-height: 1.5;
				letter-spacing: 0.07143em;
				font-weight: 400;
				font-size: 0.8rem;
				color: inherit;
				padding-bottom: 0;
			}
		}
	}
}

	@media all and (max-width: 996px) {
		div#app .v-carousel {
			&-item {
				flex-direction: column;
			}

			&-item > div:first-of-type {
				min-height: 50vw;
				max-height: 50vw;
			}

			&-item > div:last-of-type {
				padding: 4rem 2rem 1rem;

				& > p {
					font-size: 0.85rem;
				}
			}
		}
	}
</style>

<template>
	<div class="v-carousel-item">
		<div v-bind:style="image"></div>
		<div>
			<h3>{{ infoPanel.title }}</h3>
			<p>{{ infoPanel.text }}</p>
			<div v-if="infoPanel.quote.hasQuote">
				<h4 v-if="infoPanel.quote.title">{{ infoPanel.quote.title }}</h4>
				<h5 v-if="infoPanel.quote.subtitle">{{ infoPanel.quote.subtitle }}</h5>
				<p>{{ infoPanel.quote.text }}</p>
			</div>
		</div>
	</div>
</template>

<script>
export default{
	props: ['image', 'infoPanel'],
	data() {
		return {};
	},
};
</script>
