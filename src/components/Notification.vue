<template>
	<div v-if="deleted.state" class="alert alert-danger" role="alert">
		Photo with ID: {{ deleted.photo }} was deleted!!
	</div>
</template>

<script>
export default {
	props: ["deleted"],
};
</script>

<style></style>
