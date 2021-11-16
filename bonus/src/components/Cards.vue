<template>
	<div class="cards">
		<div class="d-flex justify-content-center">
			<SearchBoxGenre @search-genre="filteredGenre" :cards="cards" />
			<SearchBoxAuthor @search-author="filteredAuthor" :cards="cards" />
		</div>
		<div class="row" v-if="!loading">
			<div class="col-2" v-for="card in getAlbum" :key="card.title">
				<div class="card text-center">
					<img :src="card.poster" :alt="card.author" />
					<h2>{{ card.title.toUpperCase() }}</h2>
					<div>
						<h4>{{ card.author }}</h4>
						<h4>{{ card.year }}</h4>
					</div>
				</div>
			</div>
		</div>
		<div class="loading" v-else>Loading ...</div>
	</div>
</template>

<script>
import SearchBoxGenre from "./SearchBoxGenre.vue";
import SearchBoxAuthor from "./SearchBoxAuthor.vue";

import axios from "axios";
export default {
	data() {
		return {
			cards: [],
			loading: true,
			error: "",
			API_URL: "https://flynn.boolean.careers/exercises/api/array/music",
			searchTextGenre: "",
			searchTextAuthor: "",
		};
	},
	components: {
		SearchBoxGenre,
		SearchBoxAuthor,
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
					this.cards = r.data.response;
					this.loading = false;
				})
				.catch((e) => {
					console.log(e, "OPS!");
					this.error = `'OPS!' ${e}`;
				});
		},
		filteredGenre(text) {
			this.searchTextGenre = text;
		},
		filteredAuthor(textAuthor) {
			this.searchTextAuthor = textAuthor;
		},
	},
	computed: {
		getAlbum() {
			if (this.searchTextGenre && this.searchTextAuthor === "All") {
				return this.cards;
			} else {
				const filtered = this.cards.filter((card) => {
					return (
						card.genre.includes(this.searchTextGenre) &&
						card.author.includes(this.searchTextAuthor)
					);
				});
				return filtered;
			}
		},
	},
};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";

.cards {
	text-align: center;
}

.row {
	width: 100%;
	margin: auto !important;
	justify-content: center;
	text-align: center;
	padding-top: 3rem;
	.col-2 {
		height: auto;
		padding: 0.5rem !important;
		border: none;
		&:hover {
			cursor: pointer;
		}
		.card {
			height: 100%;
			background-color: $header_mainCard_backgroundColor !important;
			img {
				padding: 0.5rem;
			}
			h2 {
				margin: 0.5rem !important;
				font-size: 18px;
				color: #fff;
				&:hover {
					text-decoration: underline;
				}
			}
			h4 {
				font-size: 15px;
				color: #fff;
				&:hover {
					text-decoration: underline;
				}
			}
		}
	}
}

.loading {
	margin: 1rem;
	color: #fff;
}
</style>
