<template>
	<div>
		<nav>
			<NuxtLink to="/">Cocktails</NuxtLink>
			<NuxtLink to="/ingredients">Ingredients</NuxtLink>
		</nav>
		<main>
			<slot />
		</main>
	</div>
</template>

<style>
	nav {
		display: flex;
		gap: 15px;
	}
	main,
	nav {
		max-width: 1400px;
		margin: 0 auto;
	}

</style>
