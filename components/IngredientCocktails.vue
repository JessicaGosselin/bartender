<script setup>
	const { cocktails } = defineProps(['cocktails']);
</script>

<template>
	<h2>This is featured in these drinks</h2>
	<div class="ingredient-cocktails-wrapper">
		<CocktailCard v-for="cocktail in cocktails" :cocktail="cocktail"/>
	</div>
</template>

<style lang="scss">
	.ingredient-cocktails-wrapper {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 20px;
		a {
			display: flex;
			flex-direction: column;
			align-items: center;
			gap: 5px;
			text-align: center;
			color: brown;
			img {
				max-width: 100%;
			}
		}
	}	
</style>