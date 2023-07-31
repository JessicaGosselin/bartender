<script setup>
	const { name } = defineProps(['name']);
</script>

<template>
	<div>
		<NuxtLink :to="`/ingredients/${name}`">
			<h1>{{ name }}</h1>
			<img :src="`https://www.thecocktaildb.com/images/ingredients/${name}-medium.png`"/>
		</NuxtLink>
	</div>
</template>