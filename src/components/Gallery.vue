<template>
	<div class="row">
		<Notification :deleted="this.deleted"></Notification>
		<div
			v-for="photo in gallery"
			:key="photo.id"
			@click="deleteImg(photo)"
			class="col-6 col-sm-3 mb-3"
		>
			<GalleryImg :src="photo.url" />
		</div>
	</div>
</template>

<script>
import axios from "axios";
import GalleryImg from "./GalleryImg.vue";
import Notification from "./Notification.vue";
export default {
	name: "GalleryPhotos",
	components: { GalleryImg, Notification },
	data() {
		return {
			images: [],
			start: 0,
			end: 20,
			gallery: null,
			deleted: {
				state: false,
				photo: null,
			},
		};
	},
	methods: {
		async getAllImages() {
			const response = await axios.get(
				"https://jsonplaceholder.typicode.com/photos"
			);

			return response.data;
		},
		getListImages() {
			const data = this.images.slice(this.start, this.end);
			this.start += 20;
			this.end += 20;
			return data;
		},
		handleScroll() {
			if (
				window.scrollY + window.innerHeight >=
				document.body.scrollHeight - 50
			) {
				const newList = this.getListImages();
				this.gallery = [...this.gallery, ...newList];
			}
		},
		deleteImg(photo) {
			const indexOfPhoto = this.gallery.indexOf(photo);
			this.gallery.splice(indexOfPhoto, 1);

			this.deleted.state = true;
			this.deleted.photo = photo.id;
			setTimeout(() => {
				this.deleted.state = false;
			}, 3000);
		},
	},
	async mounted() {
		this.images = await this.getAllImages();
		this.gallery = this.getListImages();
		window.addEventListener("scroll", this.handleScroll);
	},

	watch: {
		// Cuando elimine y tenga imagenes menor a 8, se llamará nuevamente al método
		gallery: function (newValue) {
			if (newValue.length === 8) {
				this.gallery = [...this.gallery, ...this.getListImages()];
			}
		},
	},
};
</script>

<style></style>
