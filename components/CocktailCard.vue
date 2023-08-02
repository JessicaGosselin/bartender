<script setup>
	const { name, image, id } = defineProps(['name', 'image', 'id']);
</script>

<template>
	<div class="cocktail-card">
		<NuxtLink :to="`/cocktails/${id}`">
			<h1 class="card-title">{{ name }}</h1>
			<img :src="image"/>
		</NuxtLink>
	</div>
</template>