<template>
	<div>
		<div class="row" v-if="!loading">
			<div class="col-2" v-for="card in cards" :key="card.title">
				<div class="card">
					<img :src="card.poster" alt="" />
					<h2>{{ card.title }}</h2>
					<div>
						<h2>{{ card.author }}</h2>
						<h4>{{ card.year }}</h4>
					</div>
				</div>
			</div>
		</div>
		<div class="loading" v-else>Loading ...</div>
	</div>
</template>

<script>
import axios from "axios";
export default {
	data() {
		return {
			cards: [],
			loading: true,
			API_URL: "https://api.sampleapis.com/rickandmorty/characters",
		};
	},
	mounted() {
		setTimeout(this.callApi, 1000);
	},
	methods: {
		callApi() {
			axios
				.get(this.API_URL)
				.then((r) => {
					console.log(r.data);
					this.cards = r.data;
					this.loading = false;
				})
				.catch((e) => {
					console.log(e, "OPS!");
					this.error = `'OPS!' ${e}`;
				});
		},
	},
};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";

.row {
	width: 100%;
	margin: auto !important;
	justify-content: center;
	text-align: center;
	.col-2 {
		height: auto;
		padding: 0.5rem !important;
		border: none;
		.card {
			height: 100px;
			background-color: $header_mainCard_backgroundColor !important;
			border: none !important;
		}
	}
}

.loading {
	color: #fff;
}
</style>
