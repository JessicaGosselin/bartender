<script setup>
	const id = useRoute().params.id;
	const { data } = await useFetch('https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=' + id);
	const cocktail = ref(data.value.drinks[0]);
	const ingredients = ref([]);
	for (let i = 1; i <= 15; i++) {
		let measure = cocktail.value['strMeasure' + i];
		let ingredient = cocktail.value['strIngredient' + i];
		if (ingredient) {
			ingredients.value.push((measure) ? measure + ' ' + ingredient : ingredient);
		}
	}
</script>

<template>
	<div class="single-cocktail">
		<img :src="cocktail.strDrinkThumb"/>
		<div>
			<h1>{{ cocktail.strDrink }}</h1>
			<h2>You will need:</h2>
			<ul>
				<li v-for="ingredient in ingredients">{{ ingredient }}</li>
			</ul>
			<h2>Instructions</h2>
			<div>{{ cocktail.strInstructions }}</div>
		</div>
	</div>
</template>