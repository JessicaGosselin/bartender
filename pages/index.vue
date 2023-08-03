<script setup>
	
	const cocktails = ref([]);

	for (let i = 1; i <= 8; i++) {
		let { data : random } = await useFetch('https://www.thecocktaildb.com/api/json/v1/1/random.php', {
			key: 'random-' + i
		});
		cocktails.value.push(random.value.drinks[0]);
	}

</script>

<template>
	<div class="home">
		<h1 class="page-title">What would you like to drink?</h1>
		<CocktailFilters/>
		<CocktailList :cocktails="cocktails"/>
	</div>
</template>

<style lang="scss">
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
	}

	.single-cocktail,
	.single-ingredient {
		display: flex;
		gap: 40px;
	}

	.card {
		a {
			text-decoration: none;
		}	
		h1 {
			color: brown;
		}
	}

	.page-title {
		font-family: Lobster;
		font-size: 50px;
		text-align: center;
		margin-top: 0;
	}
</style>