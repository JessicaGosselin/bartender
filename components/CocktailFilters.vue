<script setup>
	const query = ref('');
	const searchedCocktails = ref([]);
	let alphabet = [...Array(26)].map((_, i) => String.fromCharCode(i + 65));
	alphabet.unshift('0-9');

	async function search() {
		const { data } = await useFetch('https://www.thecocktaildb.com/api/json/v1/1/search.php?s=' + query.value);
		searchedCocktails.value = data.value.drinks;
	}
</script>

<template>
	<div class="cocktail-filters">
		<NuxtLink v-for="letter in alphabet" :to="`/cocktails/by-first-letter/${letter}`">{{ letter }}</NuxtLink>
	</div>
	<form @submit.prevent="search">
		<input type="text" v-model="query" />
		<button>Have a specific cocktail in mind?</button>
		<div v-if="searchedCocktails" class="cocktails">
			<CocktailCard v-for="cocktail in searchedCocktails" :cocktail="cocktail"/>
		</div>
	</form>
	
</template>

<style lang="scss">
	.cocktail-filters {
		display: flex;
		gap: 5px;
	}
</style>