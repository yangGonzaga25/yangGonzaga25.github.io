<script>
  import { modalOpened } from '$lib/store';
	import { onMount } from 'svelte';
	let displayedText = '';
	const fullText = "            Thank you for taking the time to get to know me. Let’s connect and build something amazing together!";
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

	<!-- Add Social Icons Below -->
	<div class="icons">
		<div
			role="button"
			tabindex="0"
			on:keypress={() => {
				modalOpened.set(true);
			}}
			on:click={() => {
				modalOpened.set(true);
			}}
		>
		<a
			href="https://mail.google.com/mail/u/0/#inbox?compose=DmwnWrRmTgNDkTHwdzdPLTvJgswvpVtSwCKHMVSxpsSLmjZMGkJsQMPPgRFVLgmRDHSknfVCSFQq"
			aria-label="GitHub"
			target="_blank"
			rel="noopener noreferrer"
		>
			<div class="icon">
				<img src="/images/envelope.png" alt="Envelope" />
			</div>
		</div>
	
		<a
			href="https://github.com/yangGonzaga25"
			aria-label="GitHub"
			target="_blank"
			rel="noopener noreferrer"
		>
			<div class="icon">
				<img src="/images/github.png" alt="GitHub" />
			</div>
		</a>
		<a
			href="https://www.reddit.com/user/Any-Acanthisitta3113/"
			aria-label="Linkedin"
			target="_blank"
			rel="noopener noreferrer"
		>
			<div class="icon">
				<img src="/images/reddit.png" alt="Reddit" />
			</div>
		</a>
		<a
			href="https://www.facebook.com/tan.zzz7/"
			aria-label="Medium"
			target="_blank"
			rel="noopener noreferrer"
		>
			<div class="icon">
				<img src="/images/facebook.png" alt="Facebook" />
			</div>
		</a>
	</div>
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
		padding-left: 800px;
	}

	p {
		max-width: 80%;
		font-weight: 700;
		font-size: 2vw;
		padding-top: 170px;
		margin: 10px 10px 0;
		opacity: 0;
		animation: fadeIn 1s forwards, glow 1.5s infinite alternate;
	}

	.unique-animation {
		color: #ffffff;
		text-shadow: 
			0 0 5px #ffffff68, 
			0 0 10px #ffffff60, 
			0 0 15px #00d4ff,
			0 0 20px #0d0987;
		animation: typewriter 1s forwards, infinite alternate;
	}

	.icons {
    display: flex;
    justify-content: flex-start;
    gap: 20px;
    padding: 35rem 0;
    position: fixed;
    padding-left: 10px;
}

.icon {
    cursor: pointer;
    transition: transform 0.3s ease-in-out; /* Smooth scaling and rotation */
    width: 80px;
    height: 80px;
    position: relative;
}

.icon img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease-in-out; /* Smooth transition for image */
}

/* Hover Effect */
.icon:hover {
    animation: bounce-rotate 0.5s ease-in-out both; /* Unique hover animation */
    transform: scale(1.3); /* Increase size on hover */
}

/* Unique Bounce and Rotate Animation */
@keyframes bounce-rotate {
    0% {
        transform: scale(1) rotate(0deg);
    }
    50% {
        transform: scale(1.2) rotate(15deg); /* Bounce up with slight rotation */
    }
    100% {
        transform: scale(1.3) rotate(0deg); /* Settle down in a larger size */
    }
}

/* Animation for icon image on hover */
.icon:hover img {
    transform: scale(1.1) rotate(-10deg); /* Adds a slight tilt and zoom to the image */
}


	@keyframes fadeIn {
		0% {
			opacity: 0;
			transform: translateY(20px);
		}
		100% {
			opacity: 1;
			transform: translateY(0);
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
