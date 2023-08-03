<template>
	<header>
		<nav>
			<NuxtLink to="/">Home</NuxtLink>
			<NuxtLink to="/cocktails">Cocktails</NuxtLink>
			<NuxtLink to="/ingredients">Ingredients</NuxtLink>
		</nav>
	</header>
	<main>
		<NuxtPage/>
	</main>
</template>

<style lang="scss">

	header {
		padding-top: 25px;
		padding-bottom: 25px;
		display: flex;
		justify-content: center;
		background-color: #7b5942;
		position: sticky;
		top: 0;
	}

	nav {
		display: flex;
		gap: 50px;
		a {
			font-size: 20px;
			color: white;
			&.router-link-active {
				text-decoration: underline;
			}
		}
	}
	main,
	nav {
		max-width: min(1400px, 90vw);
		margin: 0 auto;
	}

	main {
		padding-block: 40px;
	}

	a {
		text-decoration: none;
	}

</style>
