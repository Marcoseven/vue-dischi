<template>
	<div class="container">
		<div class="contentHeader w-75">
			<img src="../assets/img/spotify-logo.svg" alt="logo Spotify" />
		</div>
	</div>
</template>

<script>
export default {};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";

.contentHeader {
	background-color: $header_mainCard_backgroundColor;
	margin: 0 auto;
	img {
		width: 4%;
		margin: 0.5rem 1rem;
	}
}
</style>
