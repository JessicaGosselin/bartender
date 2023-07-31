<script setup>
const route = useRoute();

const name = ref('');
name.value = route.params.name.toLowerCase();

const { data : ingredient } = await useFetch(`https://www.thecocktaildb.com/api/json/v1/1/search.php?i=${name.value}`);
const test = await useFetch(`https://www.thecocktaildb.com/images/ingredients/${name.value}.png/preview`);

const src = ref('');
src.value = `https://www.thecocktaildb.com/images/ingredients/${name.value}.png`;


</script>

<template>
	<div>
		<h1>{{ route.params.name }}</h1>
		<img :src="src"/>
	</div>
</template>
