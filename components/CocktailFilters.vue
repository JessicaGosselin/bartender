<script setup>
	const query = ref('');
	const emit = defineEmits(['updateCocktails']);
	let alphabet = [...Array(26)].map((_, i) => String.fromCharCode(i + 65));
	alphabet.unshift('0-9');

	async function search() {
		const { data } = await useFetch('https://www.thecocktaildb.com/api/json/v1/1/search.php?s=' + query.value);
		emit('updateCocktails', data.value.drinks);
	}
</script>

<template>
	<div class="filters-wrapper">
		<div class="letter-filters">
			<NuxtLink v-for="letter in alphabet" :to="`/cocktails/by-first-letter/${letter}`">{{ letter }}</NuxtLink>
		</div>
		<form @submit.prevent="search" class="search">
			<label>Have a specific cocktail in mind?</label>
			<input type="text" v-model="query" />
			<button>Search</button>
		</form>
	</div>
</template>

<style lang="scss">
	.filters-wrapper {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 15px;
		margin-bottom: 25px;
		.letter-filters {
			display: flex;
			gap: 10px;
			a {
				color: black;
			}
			a.router-link-active {
				font-weight: bold;
			}
		}
		.search {
			display: flex;
			label {
				font-weight: bold;
				margin-right: 10px;
			}
			input {
				margin-right: 2px;
			}
		}
	}
</style>