<script setup>
	const { data : cocktails } = await useFetch(`https://www.thecocktaildb.com/api/json/v1/1/filter.php?a=Alcoholic`);

	function updateCocktails(searchedCocktails) {
		cocktails.value = searchedCocktails;
    }
</script>

<template>
	<div>
		<h1 class="page-title">What would you like to drink?</h1>
		<CocktailFilters @updateCocktails="updateCocktails"/>
		<CocktailList :cocktails="cocktails.drinks"/>
	</div>
</template>