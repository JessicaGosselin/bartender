<script setup>
	const query = ref('');
	const searchedIngredients = ref([]);

	async function search() {
		const { data } = await useFetch('https://www.thecocktaildb.com/api/json/v1/1/search.php?i=' + query.value);
		searchedIngredients.value = data.value.ingredients;
	}
</script>

<template>
	<div class="filters-wrapper">
		<form @submit.prevent="search" class="search">
			<label>Looking for a specific ingredient?</label>
			<input type="text" v-model="query" />
			<button>Search</button>
		</form>
		<div v-if="searchedIngredients" class="ingredients">
			<IngredientCard v-for="ingredient in searchedIngredients" :name="ingredient.strIngredient"/>
		</div>
	</div>
</template>

<style lang="scss">
	.filters-wrapper {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 15px;
		margin-bottom: 25px;
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