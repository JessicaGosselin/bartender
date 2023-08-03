<script setup>
	const { cocktails } = defineProps(['cocktails']);
</script>

<template>
	<div class="cocktails" v-if="cocktails">
		<CocktailCard v-for="cocktail in cocktails" :cocktail="cocktail" />
	</div>
	<div v-else>
		<h1>Oops! There are no cocktails for this request yet!</h1>
	</div>
</template>