<script setup>
	let alphabet = [...Array(26)].map((_, i) => String.fromCharCode(i + 65));
	alphabet.unshift('0-9');
</script>

<template>
	<div class="filters">
		<NuxtLink v-for="letter in alphabet" :to="`/cocktails/by-first-letter/${letter}`">{{ letter }}</NuxtLink>
	</div>
</template>

<style lang="scss">

</style>