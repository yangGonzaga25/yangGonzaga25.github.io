<script lang="ts">
    // Importing necessary components and stores
    import { onMount } from 'svelte';
    import { page } from '$app/stores';
    import { customBackground } from '$lib/store';

    let imgSrc = '/images/tanya-profile.jpg'; // Path to your profile picture
    let name = "Tanya Grace";

    // CSS for the page
    const cssVariables = (
        node: HTMLElement,
        variables: { [key: string]: string }
    ): { update: (variables: { [key: string]: string }) => void } => {
        setCssVariables(node, variables);

        return {
            update(variables: { [key: string]: string }) {
                setCssVariables(node, variables);
            }
        };
    };

    const setCssVariables = (node: HTMLElement, variables: { [key: string]: string }): void => {
        for (const name in variables) {
            node.style.setProperty(`--${name}`, variables[name]);
        }
    };
</script>

<svelte:body use:cssVariables={{ background: 'url(/images/about-bg.jpg)' }} />

<section class="about-container">
	<div class="profile-picture">
		<img src="/images/profile.png" alt="Tanya Grace Profile" />
	</div>
	
    <div class="about-content">
        <h1>About Me</h1>
        <p>
            Hi, I’m <strong>{name}</strong>, a dedicated student developer with a strong passion for tech and a personal drive to continuously improve myself both inside and outside the classroom.
            I'm known for being a silent, dependable presence in any group, handling tasks efficiently and ensuring that everything runs smoothly—just like a processor in a computer.
        </p>

        <h2>My Personal Life</h2>
        <p>
            When I’m not working on projects, I enjoy taking care of my overall well-being. I’m committed to my fitness journey and have set routines to achieve specific goals, whether it's maintaining my skin’s glow, improving my waistline, or caring for my long hair. I also enjoy incorporating gua sha into my facial care routine and love finding natural ways to enhance my appearance, like teeth whitening.
        </p>

        <h2>Student Experience</h2>
        <p>
            My academic life is filled with exciting projects. Currently, I’m working on a system for small and medium clinics to streamline patient management and medical information. I’ve also been involved in organizing events, like quiz competitions and the upcoming sportfest for the College of Computer Studies. These experiences have helped me grow as a team player and honed my leadership and organizational skills.
        </p>

        <h2>My Journey as a Student Developer</h2>
        <p>
            As a developer, I focus on backend systems, database management, and web development using languages and frameworks like PHP, MySQL, HTML, CSS, and Svelte. My journey started with simple projects, but now, I’m working toward more complex systems, like an Efficient Appointment Scheduling System for healthcare management. I’m constantly learning and evolving, pushing my limits to contribute something meaningful to every project I’m a part of.
        </p>

        <p>
            Thank you for taking the time to get to know me. Let’s connect and build something amazing together!
        </p>
    </div>
</section>

<style>
    .about-container {
        display: flex;
        flex-direction: column;
        padding: 2rem 0 2rem 5rem; /* Adds padding to the left */
        max-width: 60%;
        margin: 0 auto;
        color: white;
    }

   .profile-picture {
    align-self: center; /* Keeps the profile image centered */
    overflow: hidden; /* Ensures no overflow when scaling */
}

.profile-picture img {
	margin-top: -180px;
	margin-bottom: -230px;
    width: 50rem;
    height: 50rem;
    border-radius: 50%;
    transition: transform 0.3s ease, box-shadow 0.3s ease; /* Smooth transition */
}

.profile-picture img:hover {
    transform: scale(1.1); /* Scale effect on hover */
}

    .about-content {
        text-align: left;
        line-height: 1.8;
        margin-left: 80px; /* Adds some margin to the left of the text */
    }

    h1 {
        font-size: 2.5rem;
        margin-bottom: 1.5rem;
		text-shadow: 0 0 10px rgba(0, 170, 255, 0.8), 0 0 20px rgba(0, 170, 255, 0.6); /* Glowing effect */

    }

    h2 {
        font-size: 1.8rem;
        margin-top: 2rem;
        color: #ffffff;
		text-shadow: 0 0 8px rgba(0, 170, 255, 0.8), 0 0 16px rgba(0, 170, 255, 0.6); /* Glowing effect */

    }

    p {
        font-size: 1.2rem;
        margin-bottom: 1rem;
		text-shadow: 0 0 8px rgb(0, 0, 0), 0 0 16px rgba(0, 0, 0, 0.6); /* Glowing effect */

    }

    @media (min-width: 600px) {
        .about-container {
            padding: 3rem 0 3rem 6rem; /* Increase left padding on larger screens */
        }

        h1 {
            font-size: 3rem;
        }

        h2 {
            font-size: 2.2rem;
        }
    }
</style>

