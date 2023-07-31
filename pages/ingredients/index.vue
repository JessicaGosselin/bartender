<script setup>
	const {data : ingredients }  = await useFetch(
	`https://www.thecocktaildb.com/api/json/v1/1/list.php?i=list`
);
</script>

<template>
	<div>
		<h1>Choose your Ingredient</h1>

		<div class="ingredients">
			<NuxtLink :to="`/ingredients/${ingredient.strIngredient1}`" v-for="ingredient in ingredients.drinks">{{ingredient.strIngredient1}}</NuxtLink>
		</div>
	</div>
</template>
