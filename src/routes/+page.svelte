<script>
	import { onMount } from 'svelte';
	
	let displayedText = '';
	const fullText = "Welcome to my world! \n I’m Tanya Grace Gonzaga,\n here to turn tech dreams\n into reality\n—one line of code at a time!";
	const typingSpeed = 50; // Speed of typing in milliseconds

	function typeWriter() {
		let index = 0;
		const textArray = fullText.split('');
		
		const interval = setInterval(() => {
			if (index < textArray.length) {
				displayedText += textArray[index];
				index++;
			} else {
				clearInterval(interval);
			}
		}, typingSpeed);
	}

	onMount(() => {
		typeWriter();
	});
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>
<main>
	<p class="unique-animation">{displayedText}</p>
</main>

<style>

	main {
		text-align: left;
		padding: 0;
		margin: 0;
		display: flex;
		flex-direction: column;
		height: calc(100vh - 80px - 88px);
		justify-content: flex-start;
		align-items: flex-start;
		padding-top: 50px;
	}

	p {
    max-width: 60%;
    font-weight: 700;
    font-size: 2vw; /* Use vw for responsive sizing */
    padding-top: 170px;
    margin: 10px 10px 0;
    opacity: 0; /* Start invisible */
    animation: fadeIn 1s forwards, glow 1.5s infinite alternate; /* Apply animations */
}

	.unique-animation {
		color: #ffffff;
		text-shadow: 
			0 0 5px #ffffff68, 
			0 0 10px #ffffff60, 
			0 0 15px #00d4ff,
			0 0 20px #0d0987;
		animation: typewriter 1s forwards,  infinite alternate; /* Apply new animations */
	}

	@keyframes fadeIn {
		0% {
			opacity: 0; /* Start invisible */
			transform: translateY(20px);
		}
		100% {
			opacity: 1;
			transform: translateY(0);
		}
	}

	@keyframes scaleRotate {
		0% {
			transform: scale(1) rotate(0deg);
			color: #ffffff;
		}
		50% {
			transform: scale(1.1) rotate(3deg);
			color: #00d4ff;
		}
		100% {
			transform: scale(1) rotate(0deg);
			color: #ffffff;
		}
	}

	@keyframes typewriter {
		0% {
			opacity: 0;
		}
		100% {
			opacity: 1;
		}
	}

	@media (min-width: 900px) {
		p {
			font-size: 48px;
		}
	}

	@media (min-width: 600px) {
		main {
			max-width: none;
		}
	}
</style>
