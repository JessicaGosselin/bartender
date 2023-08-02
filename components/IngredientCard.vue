<script setup>
	const { name } = defineProps(['name']);
</script>

<template>
	<div class="ingredient-card card">
		<NuxtLink :to="`/ingredients/${name}`">
			<h1 class="card-title">{{ name }}</h1>
			<img class="card-image" :src="`https://www.thecocktaildb.com/images/ingredients/${name}-medium.png`"/>
		</NuxtLink>
	</div>
</template>