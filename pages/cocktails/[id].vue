<script setup>
	const route = useRoute();
	const { data : cocktail } = await useFetch(`https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=${route.params.id}`);
	const drink = ref(cocktail.value.drinks[0]);
	const ingredients = ref([]);
	for (let i = 1; i <= 15; i++) {
		let measure = drink.value[`strMeasure${i}`];
		let ingredient = drink.value[`strIngredient${i}`];
		if (ingredient) {
			ingredients.value.push((measure) ? measure + ' ' + ingredient : ingredient);
		}
	}
</script>

<template>
	<div class="single-cocktail">
		<img :src="drink.strDrinkThumb"/>
		<div>
			<h1>{{ drink.strDrink }}</h1>
			<h2>You will need:</h2>
			<ul>
				<li v-for="ingredient in ingredients">{{ ingredient }}</li>
			</ul>
			<h2>Instructions</h2>
			<div>{{ drink.strInstructions }}</div>
		</div>
	</div>
</template>