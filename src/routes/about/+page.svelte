<script lang="ts">
    // Importing necessary components and stores
    import { onMount } from 'svelte';
    import { page } from '$app/stores';
    import { customBackground } from '$lib/store';

    let imgSrc = '/images/tanya-profile.jpg'; // Path to your profile picture
    let name = "Tanya Grace S. Gonzaga";

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
            Hi, I’m <strong>{name}</strong>, a dedicated student of Bachelor in Science and Information and Technology with a passion for personal drive to continuously improve myself both inside and outside the classroom.
            I'm known for being a student leader, dependable presence in any group, handling tasks efficiently and ensuring that everything runs smoothly—just like a processor in a computer.
        </p>

        <h2>My Personal Life</h2> 
        <p> 
            Outside of my school as a student developer, I enjoy a variety of activities that bring balance to my life. I have a deep appreciation for the moon and often find solace in its presence, whether I’m relaxing at home with my cats or unwinding with a good movie or anime series. I’m also passionate about outdoor adventures—whether it's traveling to new places, hiking through scenic landscapes, or camping under the stars, I always embrace the opportunity to explore. Aside that, I take on commissioned work to help support my family financially, which allows me to channel my skills into meaningful projects while contributing to the people I care about. 

        </p>
        <h2>Student Experience</h2> 
        <p> 
            Throughout my academic journey, I’ve consistently taken on leadership roles in the schools I’ve attended, and I currently serve as the secretary of ELITES. In this role, I am responsible for handling the organization’s files and ensuring that I effectively serve all BSIT students. My involvement has sharpened my organizational skills and provided me with valuable experience in managing responsibilities.
            In addition to my academic and organizational commitments, I participated as Chess Player in Sportsfest 2023, where I proudly won a gold medal for the College of Computer Studies department. These experiences—whether in project work or leadership roles—have allowed me to grow as a team player and refine my leadership abilities.
            
            </p>

        <h2>My Journey as a Student Developer</h2>
        <p>
            As a developer, I focus on both frontend and backend systems, database management, and web development using languages and frameworks like PHP, MySQL, HTML, CSS, Angular, Python, Java and Svelte. My journey started with simple projects, but now, I’m working toward more complex systems, like an Efficient Appointment Scheduling System for healthcare management. I’m constantly learning and evolving, pushing my limits to contribute something meaningful to every project I’m a part of.
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
	margin-bottom: -220px;
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

