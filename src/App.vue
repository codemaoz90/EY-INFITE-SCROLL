<template>
	<div id="app">
		<AppLayout>
			<template #header>
				<h1 class="title">
					EY-PRUEBA-TÉCNICA
					<span>Infinite Scroll</span>
				</h1>
			</template>
			<template #content>
				<GalleryPhotos />
			</template>
		</AppLayout>
	</div>
</template>

<script>
import AppLayout from "./components/Layout.vue";
import GalleryPhotos from "./components/Gallery";
export default {
	name: "App",
	components: {
		GalleryPhotos,
		AppLayout,
	},
};
</script>

<style></style>
