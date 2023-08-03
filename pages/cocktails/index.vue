<script setup>
	const { data : cocktails } = await useFetch(`https://www.thecocktaildb.com/api/json/v1/1/filter.php?a=Alcoholic`);
</script>

<template>
	<div>
		<h1 class="page-title">What would you like to drink?</h1>
		<div class="cocktails">
			<CocktailCard v-for="cocktail in cocktails.drinks" :cocktail="cocktail" />
		</div>
	</div>
</template>