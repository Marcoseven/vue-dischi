<template>
	<div id="app">
		<SiteHeader />
		<SiteMain />
	</div>
</template>

<script>
import SiteHeader from "./components/SiteHeader";
import SiteMain from "./components/SiteMain";

export default {
	name: "App",
	components: {
		SiteHeader,
		SiteMain,
	},
};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap.scss";
@import "./assets/scss/common.scss";
@import "./assets/scss/variables.scss";
</style>
