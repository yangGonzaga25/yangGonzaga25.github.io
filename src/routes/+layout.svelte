<script lang="ts">
    import "../app.css";
	import Navbar from '$lib/components/NavBar.svelte';
	import Button from '$lib/components/Button.svelte';
	import { page } from '$app/stores';
	import Modal from '$lib/components/Modal.svelte';
	import { onMount } from 'svelte';
	import { customBackground } from '$lib/store';
	import { Email } from '$lib/Constants';

	let copied = false;
	const cookieEnabled = false;
	$: showCookieModal = false;

	interface CssVariables {
		[name: string]: string;
	}

	const cssVariables = (
		node: HTMLElement,
		variables: CssVariables
	): { update: (variables: CssVariables) => void } => {
		setCssVariables(node, variables);

		return {
			update(variables: CssVariables) {
				setCssVariables(node, variables);
			}
		};
	};

	const setCssVariables = (node: HTMLElement, variables: CssVariables): void => {
		for (const name in variables) {
			node.style.setProperty(`--${name}`, variables[name]);
		}
	};

	const copy = () => {
		navigator.clipboard.writeText(Email);
	};

	const backgroundImages: { [key: string]: string } = {
		'/': 'url(/images/home-bg.gif)', // Home page background
		'/portfolio': 'url(/images/portfolio-bg.gif)', // Portfolio page background
		'/contact': 'url(/images/contact-bg.jpg)', // Contact page background
		'/about': 'url(/images/about-bg.gif)' // About page background
	};

	let currentBackground = backgroundImages['/'];

	// Update background based on the current route
	$: {
		const currentPath = $page.url.pathname;
		currentBackground = backgroundImages[currentPath] || backgroundImages['/']; // Default to home background if no match
	}

	onMount(() => {
		const showCookie = localStorage.getItem('showCookieModal');
		if (showCookie !== null) showCookieModal = JSON.parse(showCookie);
		else showCookieModal = true;
	});
</script>

<svelte:body use:cssVariables={{ background: currentBackground }} />

{#if showCookieModal && cookieEnabled}
	<div class="cookieContainer">
		<p> This website uses <a href="privacy-policy">Cookies.</a></p>
		<div
			role="button"
			tabindex="0"
			on:keypress={() => {
				showCookieModal = false;
				localStorage.setItem('showCookieModal', 'false');
			}}
			on:click={() => {
				showCookieModal = false;
				localStorage.setItem('showCookieModal', 'false');
			}}
		>
			&#10005;
		</div>
	</div>
{/if}

<Navbar segment={$page.url.pathname} />

<slot />

<style>
	* {
		box-sizing: border-box;
	}

	@font-face {
    font-family: 'Ubuntu Mono';
    font-display: swap;
    src: url('https://fonts.googleapis.com/css2?family=Ubuntu+Mono:wght@400&display=swap');
}
	:global(#svelte) {
		width: 100%;
		display: flex;
		flex-direction: column;
		flex: 1;
		padding: 1rem;
	}

	:global(html),
	:global(body) {
		transition: background-color 0.2s ease 0s;
		position: relative;
		width: 100%;
		height: 100%;
		overflow: auto;
		font-family: 'Ubuntu Mono', monospace; /* Apply Ubuntu Mono font */
	}

/* Additional styles (optional) */
h1, h2, h3, h4, h5, h6 {
    font-family: 'Ubuntu Mono', monospace; /* Apply Ubuntu Mono font */
}
	:global(body) {
		background-size: cover;
		background-position: center;
		transition: background-image 0.5s ease-in-out;
		background-image: var(--background);
		color: white;
		margin: 0;
		box-sizing: border-box;
		line-height: 1.75;
		display: flex;
		flex-direction: column;
		min-height: 100vh;
		width: 100%;
		overflow-x: hidden;
	}

	:global(h1) {
		border: 0;
		width: 100%;
	}

	:global(::selection) {
		color: white;
		background: #ca3c25;
		width: 100%;
	}

	:global(::-webkit-scrollbar) {
		width: 8px;
		height: 8px;
		border-radius: 1px;
		width: 100%;
	}

	:global(::-webkit-scrollbar-thumb) {
		background-color: #fafffd;
		border-radius: 3px;
		width: 100%;
	}

	:global(::-webkit-scrollbar-track) {
		background-color: transparent;
		border-radius: 1px;
	}

	@media (min-width: 900px) {
		:global(body) {
			padding: 0 100px;
		}
	}

	:global(a) {
		text-decoration: none;
	}

	a {
		color: rgb(0, 100, 200);
	}

	a:hover {
		text-decoration: underline;
	}

	a:visited {
		color: rgb(0, 80, 160);
	}

	.cookieContainer {
		background: white;
		border-radius: 0px;
		text-align: center;
		width: 100%;
		height: 30px;
		color: black;
		padding: 30px;
		display: flex;
		justify-content: space-evenly;
		align-items: center;
		position: fixed;
		bottom: 0px;
		left: 0;
		right: 0;
		margin-left: auto;
		margin-right: auto;
	}

	.cookieContainer > p > a {
		text-decoration: underline;
	}

	.cookieContainer > div {
		cursor: pointer;
	}

	@media (min-width: 600px) {
		.cookieContainer {
			background: white;
			border-radius: 50px;
			width: 350px;
			height: 30px;
			padding: 0 10px;
			display: flex;
			justify-content: space-evenly;
			align-items: center;
			position: fixed;
			bottom: 50px;
			left: 0;
			right: 0;
			margin-left: auto;
			margin-right: auto;
		}
	}

	@media (min-width: 900px) {
		#svelte {
			padding: 2rem 5rem;
		}
		body {
			padding: 0;
		}
	}
</style>
