<script setup>
	const { data : ingredients }  = await useFetch(`https://www.thecocktaildb.com/api/json/v1/1/list.php?i=list`);
</script>

<template>
	<div>
		<h1 class="page-title">Which ingredient would you fancy today?</h1>
		<div class="ingredients">
			<IngredientCard v-for="ingredient in ingredients.drinks" :name="`${ingredient.strIngredient1}`"/>
		</div>
	</div>
</template>
