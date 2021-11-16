<template>
	<div class="SearchBoxAuthor">
		<label for="author">Scegli l'artita: </label>
		<select
			name="author"
			id="author"
			v-model="searchAuthor"
			@change="$emit('search-author', searchAuthor)"
		>
			<option value="All">All</option>
			<option value="Bon Jovi">Bon Jovi</option>
			<option value="Queen">Queen</option>
			<option value="Sting">Sting</option>
			<option value="Steve Gadd Band">Steve Gadd Band</option>
			<option value="Iron Maiden">Iron Maiden</option>
			<option value="Eric Clapton">Eric Clapton</option>
			<option value="Deep Purple">Deep Purple</option>
			<option value="Metallica">Metallica</option>
			<option value="Dave Weckl">Dave Weckl</option>
			<option value="Michael Jackson">Michael Jackson</option>
		</select>
	</div>
</template>

<script>
export default {
	data() {
		return {
			searchAuthor: "",
		};
	},
};
</script>

<style lang="scss">
.SearchBoxAuthor {
	padding: 0.5rem;
	label {
		color: #fff;
		padding: 0 0.5rem;
	}
}
</style>
