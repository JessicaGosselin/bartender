<script setup>
	const { name, image, id } = defineProps(['name', 'image', 'id']);
</script>

<template>
	<div>
		<NuxtLink :to="`/cocktails/${id}`">
			<h1>{{ name }}</h1>
			<img :src="image"/>
		</NuxtLink>
	</div>
</template>