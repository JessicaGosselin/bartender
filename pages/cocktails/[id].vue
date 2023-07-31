<script setup>
	const route = useRoute();
	const { data : cocktail } = await useFetch(`https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=${route.params.id}`);
	const drink = ref(cocktail.value.drinks[0]);
</script>

<template>
	<div>
		<h1>{{ drink.strDrink }}</h1>
		<img :src="drink.strDrinkThumb"/>
	</div>
</template>
