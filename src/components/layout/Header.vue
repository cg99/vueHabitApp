<template>
	<header class="header">
		<h1>Habits</h1>
		<div id="nav">
			<router-link to="/">Home</router-link> |
			<router-link to="/about">About</router-link>
		</div>
	</header>
</template>

<script>
	export default {
		name: "Header"
	}
</script>

<style lang="scss" scoped>
   @import '../test/src/assets/scss/modules/header.scss';
</style>
