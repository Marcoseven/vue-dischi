<template>
	<div class="SearchBoxGenre">
		<label for="genre">Scegli il genere: </label>
		<select
			name="genre"
			id="genre"
			v-model="searchGenre"
			@change="$emit('search-genre', searchGenre)"
		>
			<option value="All">All</option>
			<option value="Rock">Rock</option>
			<option value="Pop">Pop</option>
			<option value="Jazz">Jazz</option>
			<option value="Metal">Metal</option>
		</select>
	</div>
</template>

<script>
export default {
	data() {
		return {
			searchGenre: "",
		};
	},
};
</script>

<style lang="scss">
.SearchBoxGenre {
	padding: 0.5rem;
	label {
		color: #fff;
		padding: 0 0.5rem;
	}
}
</style>
