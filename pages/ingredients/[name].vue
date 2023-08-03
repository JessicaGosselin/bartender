<script setup>
	const name = useRoute().params.name;
	const { data } = await useFetch('https://www.thecocktaildb.com/api/json/v1/1/search.php?i=' + name);
	const ingredient = ref(data.value.ingredients[0]);
	const { data : cocktails } = await useFetch('https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=' + name);
</script>

<template>
	<div class="single-ingredient">
		<img :src="`https://www.thecocktaildb.com/images/ingredients/${name}.png`"/>
		<div class="single-content">
			<button @click="$router.go(-1)">Go back</button>
			<h1>{{ name }}</h1>
			<IngredientCocktails :cocktails="cocktails.drinks"/>
			<br><br>
			<p class="type" v-if="ingredient.strType"><strong>Type :</strong> {{ ingredient.strType }}</p>
			<p class="alcoholic" v-if="ingredient.strAlcohol"><strong>Alcoholic? :</strong> {{ ingredient.strAlcohol }}</p>
			<p class="description">{{ ingredient.strDescription }}</p>
		</div>
	</div>
</template>
