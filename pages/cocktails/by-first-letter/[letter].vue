<script setup>
	const letter = useRoute().params.letter;
	const drinks = ref([]);
	
	if (letter == '0-9') {
		for (let i = 0; i <= 9; i++) {
			let { data : cocktails } = await useFetch('https://www.thecocktaildb.com/api/json/v1/1/search.php?f=' + i);
			if (cocktails.value.drinks) drinks.value.push(...cocktails.value.drinks);
		}
	} else {
		const { data : cocktails } = await useFetch('https://www.thecocktaildb.com/api/json/v1/1/search.php?f=' + letter);
		drinks.value = cocktails.value.drinks;
	}

	function updateCocktails(searchedCocktails) {
		drinks.value = searchedCocktails;
    }

</script>

<template>
	<div>
		<h1 class="page-title">What would you like to drink?</h1>
		<CocktailFilters @updateCocktails="updateCocktails"/>
		<CocktailList :cocktails="drinks"/>
	</div>
</template>