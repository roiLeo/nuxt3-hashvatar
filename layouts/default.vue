<template>
	<div>
		<header class="flex flex-col justify-center px-8">
			<nav
				class="
					flex
					items-center
					justify-end
					w-full
					relative
					max-w-2xl
					border-gray-200
					dark:border-gray-700
					mx-auto
					pt-8
					pb-8
					sm:pb-16
					text-gray-900
					bg-opacity-60
					dark:text-gray-100
				"
			>
				<ThemeSwitcher />
			</nav>
		</header>
		<main
        	class="flex flex-col justify-center px-8"
      	>
			<slot />
		</main>
	</div>
</template>

<script lang="ts">
export default {
	head: {
		bodyAttrs: {
			class: 'bg-gray-50 dark:bg-gray-900 text-white dark:text-black',
		},
	},
}
</script>

<style>
@windicss base;
@windicss components;
@windicss utilities;

::selection {
  background-color: #47a3f3;
  color: #fefefe;
}

::-moz-focus-inner {
    border-style: none;
    padding: 0;
}

html {
  min-width: 360px;
  scroll-behavior: smooth;
}

#__nuxt {
  @apply bg-gray-50 dark:bg-gray-900;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

button:focus {
	outline: 0!important;
}
</style>