<script setup>
	const route = useRoute();
	const { data : cocktails } = await useFetch(`https://www.thecocktaildb.com/api/json/v1/1/filter.php?a=Alcoholic`);
</script>

<template>
	<div>
		<h1>What would you like to drink?</h1>
		<div class="cocktails">
			<CocktailCard v-for="cocktail in cocktails.drinks" :name="cocktail.strDrink" :image="cocktail.strDrinkThumb" :id="cocktail.idDrink"/>
		</div>
	</div>
</template>

<style lang="scss">
	body {
		background-color: #fbf6e1;
	}

	.ingredients,
	.cocktails {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 30px;
		img {
			max-width: 100%;
		}
	}
</style>