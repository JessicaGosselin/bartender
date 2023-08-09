<script setup>
	
	const cocktails = ref([]);

	for (let i = 1; i <= 8; i++) {
		let { data : random } = await useFetch('https://www.thecocktaildb.com/api/json/v1/1/random.php', {
			key: 'random-' + i
		});
		cocktails.value.push(random.value.drinks[0]);
	}

	function updateCocktails(searchedCocktails) {
		cocktails.value = searchedCocktails;
    }

</script>

<template>
	<div class="home">
		<h1 class="page-title">What would you like to drink?</h1>
		<CocktailFilters @updateCocktails="updateCocktails"/>
		<CocktailList :cocktails="cocktails"/>
	</div>
</template>

<style lang="scss">

	* {
		box-sizing: border-box;
	}

	body {
		background-color: #fbf6e1;
		margin: 0;
	}

	.ingredients,
	.cocktails {
		display: grid;
		grid-template-columns: repeat(5, 1fr);
		gap: 30px;
		img {
			max-width: 100%;
		}
	}

	.home .cocktails {
		grid-template-columns: repeat(4, 1fr);
		.cocktail-card {
			.card-title {
				font-size: 24px;
			}
		}
	}

	.single-cocktail,
	.single-ingredient {
		display: flex;
		gap: 40px;
		align-items: flex-start;
		img {
			object-fit: contain;
		}
		.single-content {
			width: 100%;
		}
	}

	.card {
		a {
			display: flex;
			flex-direction: column;
			height: 100%;
			align-items: center;
			text-align: center;
			text-decoration: none;
			
		}	
		h1 {
			color: white;
			flex-grow: 1;
			display: flex;
			align-items: center;
			min-width: 100%;
			justify-content: center;
			text-align: center;
			margin: 0;
			line-height: 1.2;
			font-size: 22px;
			padding: 10px 5px;
			max-width: fit-content;
			background-color: #7b5942;
		}
	}

	.ingredient-card .card-image {
		margin-top: 15px;
	}

	.page-title {
		font-family: Lobster;
		font-size: 50px;
		text-align: center;
		margin-top: 0;
	}
</style>