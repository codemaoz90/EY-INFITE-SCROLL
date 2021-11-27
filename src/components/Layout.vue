<template>
	<div>
		<header class="header">
			<slot name="header"> </slot>
		</header>

		<main class="content">
			<div class="container">
				<slot name="content"> </slot>
			</div>
		</main>
	</div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.header {
	padding: 60px;
	text-align: center;
	background: #1abc9c;
	color: white;

	margin-bottom: 20px;

	& .title {
		color: white;

		span {
			font-style: italic;
			font-size: 1.5rem;
			display: block;
		}
	}
	@media (max-width: 450px) {
		padding: 30px;
		& .title {
			font-size: 1rem;
		}
	}
}
</style>
