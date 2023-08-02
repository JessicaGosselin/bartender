<script setup>
	const { cocktail } = defineProps(['cocktail']);
</script>

<template>
	<div class="cocktail-card card">
		<NuxtLink :to="`/cocktails/${cocktail.idDrink}`">
			<h1 class="card-title">{{ cocktail.strDrink }}</h1>
			<img class="card-image" :src="cocktail.strDrinkThumb"/>
		</NuxtLink>
	</div>
</template>