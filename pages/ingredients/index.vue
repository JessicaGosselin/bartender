<script setup>
	const { data: ingredients } = await useFetch(
	`www.thecocktaildb.com/api/json/v1/1/list.php?i=list`
);
</script>

<template>
	<div>
	<h1>Choose your Ingredient</h1>
		
	<div class="ingredients">
		<div v-for="ingredient in ingredients">{{ingredient}}</div>

	</div>
</template>
