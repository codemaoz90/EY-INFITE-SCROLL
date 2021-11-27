<template>
	<transition name="fade">
		<div v-if="deleted.state" class="alert alert-danger" role="alert">
			Photo with ID: {{ deleted.photo }} was deleted!!
		</div>
	</transition>
</template>

<script>
export default {
	props: ["deleted"],
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
	transition: opacity 1s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
	opacity: 0;
}
</style>
