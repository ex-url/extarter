<script>
	import '../app.css';
	import Header from './Header.svelte';
	import Footer from './Footer.svelte';
	import { fly, fade } from 'svelte/transition';

	let { children, data } = $props();
</script>

<div id="app" class="flex min-h-screen flex-col justify-between bg-white dark:bg-black">
	<Header></Header>
	<main class="flex-1">
		{#key data.url}
			<div
				class="page-content"
				in:fly={{ y: 20, delay: 200, start: 0 }}
				out:fade={{ duration: 200 }}
			>
				{@render children()}
			</div>
		{/key}
	</main>
	<Footer></Footer>
</div>

<style>
	@font-face {
		font-family: 'Nunito';
		src:
			url('/fonts/nunito/Nunito-Light.ttf') format('ttf'),
			url('/fonts/nunito/Nunito-Regular.ttf') format('ttf'),
			url('/fonts/nunito/Nunito-Bold.ttf') format('ttf');
		font-weight: 400;
		font-style: normal;
		font-display: swap;
	}
	:global(html.dark) {
		background-color: #000;
	}
	:global(body) {
		max-width: 1920px;
		margin: 0 auto;
		font-family: 'Nunito';
	}
	:global(.container) {
		max-width: 980px;
	}
</style>
