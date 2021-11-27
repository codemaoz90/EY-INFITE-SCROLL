<template>
	<div>
		<img :src="src" alt="" class="img-fluid blur" />
	</div>
</template>

<script>
export default {
	props: ["src", "description"],
};
</script>

<style></style>
