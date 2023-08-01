<script setup>
	const route = useRoute();
	const { data : ingredient } = await useFetch(`https://www.thecocktaildb.com/api/json/v1/1/search.php?i=${route.params.name}`);
</script>

<template>
	<div class="single-ingredient">
		<img :src="`https://www.thecocktaildb.com/images/ingredients/${route.params.name}.png`"/>
		<div>
			<h1>{{ route.params.name }}</h1>
		</div>
	</div>
</template>
