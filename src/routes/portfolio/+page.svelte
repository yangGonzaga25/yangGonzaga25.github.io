<script lang="ts">
    // Array of image paths with corresponding titles
    let projects = [
        { src: '/images/gallery1.jpg', title: 'Freshman Year' },
        { src: '/images/gallery2.jpg', title: 'First Project Presentation' },
        { src: '/images/gallery3.jpg', title: 'Coding Workshop' },
        { src: '/images/gallery4.jpg', title: 'Group Study Session' },
        { src: '/images/gallery5.jpg', title: 'Hackathon Event' }
    ];

    let relevantWorks = [
        { src: '/images/gallery6.jpg', title: 'Sportfest' },
        { src: '/images/gallery7.jpg', title: 'Software Development Class' },
        { src: '/images/gallery8.jpg', title: 'Web Design Presentation' },
        { src: '/images/gallery9.jpg', title: 'Team VitalSync' },
        { src: '/images/gallery10.jpg', title: 'Database Class' }
    ];

    let webinarCertificates = [
        { src: '/images/gallery11.jpg', title: 'Tech Meet-up' },
        { src: '/images/gallery12.jpg', title: 'Final Exam Prep' },
        { src: '/images/gallery13.jpg', title: 'Learning GitHub' },
        { src: '/images/gallery14.jpg', title: 'Collaborative Project' },
        { src: '/images/gallery15.jpg', title: 'Seminar Participation' },
        { src: '/images/gallery16.jpg', title: 'Event Volunteering' },
        { src: '/images/gallery17.jpg', title: 'Software Demo' },
        { src: '/images/gallery18.jpg', title: 'Senior Year' },
        { src: '/images/gallery19.jpg', title: 'Graduation Day' },
        { src: '/images/gallery20.jpg', title: 'Farewell Party' }
    ];
</script>

<section class="gallery-container">
    <h1>My Portfolio</h1>

    <!-- Projects Section -->
    <h2>Projects</h2>
    <div class="gallery-grid">
        {#each projects as project (project.src)}
            <div class="gallery-item">
                <img src={project.src} alt={project.title} />
                <div class="caption">{project.title}</div> <!-- Image title -->
            </div>
        {/each}
    </div>

    <!-- Relevant Works Section -->
    <h2>Relevant Works</h2>
    <div class="gallery-grid">
        {#each relevantWorks as work (work.src)}
            <div class="gallery-item">
                <img src={work.src} alt={work.title} />
                <div class="caption">{work.title}</div> <!-- Image title -->
            </div>
        {/each}
    </div>

    <!-- Webinar Certificates Section -->
    <h2>Webinar Certificates</h2>
    <div class="gallery-grid">
        {#each webinarCertificates as certificate (certificate.src)}
            <div class="gallery-item">
                <img src={certificate.src} alt={certificate.title} />
                <div class="caption">{certificate.title}</div> <!-- Image title -->
            </div>
        {/each}
    </div>
</section>

<style>
    .gallery-container {
        padding: 2rem;
        text-align: center;
        background-color: #0101015b;
        color: #333;
        border: 2px solid rgba(255, 255, 255, 0.3); /* Light border */
        border-radius: 10px; /* Rounded corners */
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5); /* Soft shadow */
        transition: transform 0.3s ease; /* Transition for hover effect */
    }

    .gallery-container:hover {
        transform: scale(1.02); /* Slight scale effect on hover */
    }

    h1 {
		margin-top: -2rem;

        font-size: 3rem;
        margin-bottom: -4rem;
        color: #ffffff;
    }

    h2 {
        font-size: 2rem;
        margin-top: 3rem;
        margin-bottom: 1.5rem;
        color: #ffffff; /* Highlight section headers */
        border-bottom: 2px solid #00aaff;
        display: inline-block;
        padding-bottom: 0.5rem;
    }

    .gallery-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); /* Responsive grid */
        gap: 1rem;
        width: 100%;
    }

    .gallery-item {
        position: relative;
        overflow: hidden;
        border-radius: 8px;
    }

    .gallery-item img {
        width: 100%;
        height: 100%;
        object-fit: cover; /* Maintain image proportions */
        border-radius: 8px;
        transition: transform 0.3s ease;
    }

    .gallery-item img:hover {
        transform: scale(1.05); /* Zoom effect on hover */
    }

    .caption {
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(0, 0, 0, 0.7); /* Semi-transparent background */
        color: white;
        padding: 10px;
        text-align: center;
        font-size: 1.2rem;
        opacity: 0; /* Start invisible */
        transition: opacity 0.3s ease; /* Transition effect */
    }

    .gallery-item:hover .caption {
        opacity: 1; /* Show caption on hover */
    }

    @media (max-width: 600px) {
        h1 {
            font-size: 2.5rem;
        }

        h2 {
            font-size: 1.5rem;
        }

        .caption {
            font-size: 1rem;
        }

        .gallery-item img {
            border-radius: 4px;
        }
    }
</style>
