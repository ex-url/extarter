<script>
	import { page } from '$app/stores';
</script>

<div class="logo">
	{#if $page.url.pathname !== '/'}
		<a href="/" class="flex items-center">
			<span class="flex h-6 w-6 items-center justify-center text-blue-600 dark:text-yellow-600">
				<svg
					xmlns="http://www.w3.org/2000/svg"
					width="100"
					height="100"
					fill="currentColor"
					viewBox="0 0 16 16"
				>
					<path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14m0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16" />
					<path
						d="M10 8a2 2 0 1 1-4 0 2 2 0 0 1 4 0M8 4a4 4 0 0 0-4 4 .5.5 0 0 1-1 0 5 5 0 0 1 5-5 .5.5 0 0 1 0 1m4.5 3.5a.5.5 0 0 1 .5.5 5 5 0 0 1-5 5 .5.5 0 0 1 0-1 4 4 0 0 0 4-4 .5.5 0 0 1 .5-.5"
					/>
				</svg>
			</span>
			<span class="ml-3 text-xl font-bold text-black dark:text-white">extarter</span>
		</a>
	{:else}
		<span class="flex items-center">
			<span class="flex h-6 w-6 items-center justify-center text-blue-600 dark:text-yellow-600">
				<svg
					xmlns="http://www.w3.org/2000/svg"
					width="100"
					height="100"
					fill="currentColor"
					viewBox="0 0 16 16"
				>
					<path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14m0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16" />
					<path
						d="M10 8a2 2 0 1 1-4 0 2 2 0 0 1 4 0M8 4a4 4 0 0 0-4 4 .5.5 0 0 1-1 0 5 5 0 0 1 5-5 .5.5 0 0 1 0 1m4.5 3.5a.5.5 0 0 1 .5.5 5 5 0 0 1-5 5 .5.5 0 0 1 0-1 4 4 0 0 0 4-4 .5.5 0 0 1 .5-.5"
					/>
				</svg>
			</span>
			<span class="ml-3 text-xl font-bold text-black dark:text-white">extarter</span>
		</span>
	{/if}
</div>

<style>
	.logo svg {
		animation: rotate 1s linear infinite;
	}
</style>
