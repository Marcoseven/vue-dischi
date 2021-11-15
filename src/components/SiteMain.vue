<template>
	<div class="container">
		<div class="contentMain">
			<Cards />
		</div>
	</div>
</template>

<script>
import Cards from "./Cards.vue";

export default {
	components: {
		Cards,
	},
};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";

.contentMain {
	height: 100vh;
	background-color: $main_backgroundColor;
	margin: 0 auto;
}
</style>
