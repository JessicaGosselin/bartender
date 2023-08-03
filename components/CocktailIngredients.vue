<script setup>
	const { ingredients } = defineProps(['ingredients']);
	const isDisplayList = ref(false);
</script>

<template>
	<div class="cocktail-ingredients-header">
		<h2>You will need</h2>
		<button @click="isDisplayList = !isDisplayList">{{ isDisplayList ? 'Grid Mode' : 'List Mode' }}</button>
	</div>
	<div class="cocktail-ingredients-wrapper">
		<template v-if="isDisplayList">
			<div class="cocktail-ingredients-list">
				<ul>
					<li v-for="ingredient in ingredients">{{ (ingredient.measure) ? ingredient.measure + ' ' + ingredient.name : ingredient.name }}</li>
				</ul>
			</div>
		</template>
		<template v-else>
			<div class="cocktail-ingredients-grid">
				<NuxtLink v-for="ingredient in ingredients" :to="`/ingredients/${ingredient.name}`">
					<img class="card-image" :src="`https://www.thecocktaildb.com/images/ingredients/${ingredient.name}-small.png`"/>
					<div>{{ (ingredient.measure) ? ingredient.measure + ' ' + ingredient.name : ingredient.name }}</div>
				</NuxtLink>
			</div>
		</template>
	</div>
</template>

<style lang="scss">
	.cocktail-ingredients-header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		button {
			flex-grow: 0;
			flex-shrink: 1;
			height: fit-content;
		}
	}
	.cocktail-ingredients-wrapper {
		ul {
			margin: 0;
			padding: 0;
			list-style-position: inside;
		}
		.cocktail-ingredients-grid {
			display: grid;
			grid-template-columns: repeat(3, 1fr);
			gap: 20px;
			a {
				display: flex;
				flex-direction: column;
				align-items: center;
				gap: 5px;
				max-width: 150px;
				text-align: center;
				color: brown;
			}
		}
	}	
</style>