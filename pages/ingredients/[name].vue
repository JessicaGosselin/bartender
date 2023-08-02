<script setup>
	const name = useRoute().params.name;
	const { data } = await useFetch('https://www.thecocktaildb.com/api/json/v1/1/search.php?i=' + name);
	const ingredient = ref(data.value.ingredients[0]);
</script>

<template>
	<div class="single-ingredient">
		<img :src="`https://www.thecocktaildb.com/images/ingredients/${name}.png`"/>
		<div>
			<h1>{{ name }}</h1>
			<div class="type">Type : {{ ingredient.strType }}</div>
			<div class="alcoholic">Alcoholic? : {{ ingredient.strAlcohol }}</div>
			<div class="description">{{ ingredient.strDescription }}</div>
		</div>
	</div>
</template>
