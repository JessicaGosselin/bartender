<script setup>
	const { data : ingredients }  = await useFetch(
	`https://www.thecocktaildb.com/api/json/v1/1/list.php?i=list`
);
</script>

<template>
	<div>
		<h1>Choose your Ingredient</h1>

		<div class="ingredients">
			<IngredientCard v-for="ingredient in ingredients.drinks" :name="`${ingredient.strIngredient1}`"/>
		</div>
	</div>
</template>

<style lang="scss">
	.ingredients {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 30px;
	}
</style>