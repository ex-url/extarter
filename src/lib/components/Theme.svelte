<script>
	import { onMount } from 'svelte';

	let button;
	let dark = $state(false);

	onMount(() => {
		if (button.ownerDocument.documentElement.classList.contains('dark')) {
			dark = true;
		}
	});

	function toggle(e) {
		dark = e.target.ownerDocument.documentElement.classList.toggle('dark');

		if (e.target.ownerDocument === document) {
			localStorage.setItem('theme', dark ? 'dark' : 'light');
		}
	}
</script>

<svelte:head>
	<script>
		if ('theme' in localStorage) {
			localStorage.getItem('theme') === 'dark'
				? window.document.documentElement.classList.add('dark')
				: window.document.documentElement.classList.remove('dark');
		} else {
			if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
				window.document.documentElement.classList.add('dark');
			}
		}
	</script>
</svelte:head>

<button
	aria-label="theme toggler"
	class="theme-toggle {dark
		? 'dark'
		: ''} relative ml-3 h-8 w-8 overflow-hidden rounded-xl bg-gray-100 text-blue-600 dark:bg-gray-900 dark:text-yellow-500"
	onclick={toggle}
	bind:this={button}
>
	<span class="sun absolute block p-2">
		<svg
			width="24"
			height="24"
			viewBox="0 0 24 24"
			fill="currentColor"
			xmlns="http://www.w3.org/2000/svg"
		>
			<path
				d="M12 19.25C8 19.25 4.75 16 4.75 12C4.75 8 8 4.75 12 4.75C16 4.75 19.25 8 19.25 12C19.25 16 16 19.25 12 19.25ZM12 6.25C8.83 6.25 6.25 8.83 6.25 12C6.25 15.17 8.83 17.75 12 17.75C15.17 17.75 17.75 15.17 17.75 12C17.75 8.83 15.17 6.25 12 6.25Z"
			/>
			<path
				d="M12 22.96C11.45 22.96 11 22.55 11 22V21.92C11 21.37 11.45 20.92 12 20.92C12.55 20.92 13 21.37 13 21.92C13 22.47 12.55 22.96 12 22.96ZM19.14 20.14C18.88 20.14 18.63 20.04 18.43 19.85L18.3 19.72C17.91 19.33 17.91 18.7 18.3 18.31C18.69 17.92 19.32 17.92 19.71 18.31L19.84 18.44C20.23 18.83 20.23 19.46 19.84 19.85C19.65 20.04 19.4 20.14 19.14 20.14ZM4.86 20.14C4.6 20.14 4.35 20.04 4.15 19.85C3.76 19.46 3.76 18.83 4.15 18.44L4.28 18.31C4.67 17.92 5.3 17.92 5.69 18.31C6.08 18.7 6.08 19.33 5.69 19.72L5.56 19.85C5.37 20.04 5.11 20.14 4.86 20.14ZM22 13H21.92C21.37 13 20.92 12.55 20.92 12C20.92 11.45 21.37 11 21.92 11C22.47 11 22.96 11.45 22.96 12C22.96 12.55 22.55 13 22 13ZM2.08 13H2C1.45 13 1 12.55 1 12C1 11.45 1.45 11 2 11C2.55 11 3.04 11.45 3.04 12C3.04 12.55 2.63 13 2.08 13ZM19.01 5.99C18.75 5.99 18.5 5.89 18.3 5.7C17.91 5.31 17.91 4.68 18.3 4.29L18.43 4.16C18.82 3.77 19.45 3.77 19.84 4.16C20.23 4.55 20.23 5.18 19.84 5.57L19.71 5.7C19.52 5.89 19.27 5.99 19.01 5.99ZM4.99 5.99C4.73 5.99 4.48 5.89 4.28 5.7L4.15 5.56C3.76 5.17 3.76 4.54 4.15 4.15C4.54 3.76 5.17 3.76 5.56 4.15L5.69 4.28C6.08 4.67 6.08 5.3 5.69 5.69C5.5 5.89 5.24 5.99 4.99 5.99ZM12 3.04C11.45 3.04 11 2.63 11 2.08V2C11 1.45 11.45 1 12 1C12.55 1 13 1.45 13 2C13 2.55 12.55 3.04 12 3.04Z"
			/>
		</svg>
	</span>
	<span class="moon absolute block p-2">
		<svg
			width="24"
			height="24"
			viewBox="0 0 24 24"
			fill="currentColor"
			xmlns="http://www.w3.org/2000/svg"
		>
			<path
				d="M12.4604 22.7501C12.2904 22.7501 12.1204 22.7501 11.9504 22.7401C6.35044 22.4901 1.67044 17.9801 1.28044 12.4801C0.940437 7.76011 3.67044 3.35011 8.07044 1.50011C9.32044 0.980114 9.98044 1.38011 10.2604 1.67011C10.5404 1.95011 10.9304 2.60011 10.4104 3.79011C9.95044 4.85011 9.72044 5.98011 9.73044 7.14011C9.75044 11.5701 13.4304 15.3301 17.9204 15.5101C18.5704 15.5401 19.2104 15.4901 19.8304 15.3801C21.1504 15.1401 21.7004 15.6701 21.9104 16.0101C22.1204 16.3501 22.3604 17.0801 21.5604 18.1601C19.4404 21.0601 16.0704 22.7501 12.4604 22.7501ZM2.77044 12.3701C3.11044 17.1301 7.17044 21.0301 12.0104 21.2401C15.3004 21.4001 18.4204 19.9001 20.3404 17.2801C20.4904 17.0701 20.5604 16.9201 20.5904 16.8401C20.5004 16.8301 20.3404 16.8201 20.0904 16.8701C19.3604 17.0001 18.6004 17.0501 17.8504 17.0201C12.5704 16.8101 8.25044 12.3801 8.22044 7.16011C8.22044 5.78011 8.49044 4.45011 9.04044 3.20011C9.14044 2.98011 9.16044 2.83011 9.17044 2.75011C9.08044 2.75011 8.92044 2.77011 8.66044 2.88011C4.85044 4.48011 2.49044 8.30011 2.77044 12.3701Z"
			/>
		</svg>
	</span>
</button>

<style>
	.theme-toggle {
		transition: all 0.3s ease;
	}
	.theme-toggle > span {
		left: 0;
		top: 0;
		width: 100%;
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
		transition: all 0.3s ease;
	}
	.sun {
		transform: translateY(100%);
	}
	.dark .sun {
		transform: translateY(0);
	}
	.moon {
		transform: translateY(0);
	}
	.dark .moon {
		transform: translateY(-100%);
	}
</style>
