<template>
	<div>
		<nav>
			<NuxtLink to="/">Home</NuxtLink>
			<NuxtLink to="/ingredients">Ingredients</NuxtLink>
		</nav>
		<slot />
	</div>
</template>

<style>
	nav {
		display: flex;
		gap: 15px;
	}
</style>
