<script lang="ts">
	import { browser } from '$app/environment';
	import Button from './Button.svelte';
	import InstagramIcon from '$lib/icons/InstagramIcon.svelte';
	import LinkedInIcon from '$lib/icons/LinkedInIcon.svelte';
	import LinkIcon from '$lib/icons/LinkIcon.svelte';
	import Badge from '$lib/components/Badge.svelte';

	const instagramIcon = InstagramIcon,
		linkedInIcon = LinkedInIcon,
		linkIcon = LinkIcon;

	const skills: Array<Array<string>> = [
		[
			'Java',
			'Spring Boot',
			'Python',
			'Django',
			'JavaScript',
			'TypeScript',
			'Vue.js',
			'MySQL',
			'ELK Stack',
			'Docker',
			'REST'
		],
		['Java', 'Jersey Framework', 'JavaScript', 'AngularJS', 'Oracle Database', 'REST']
	];

	if (browser) {
		type sectionID = 'about' | 'experience' | 'highlighted-projects';
		type sectionIDRecords = Record<
			sectionID,
			{
				name: string;
				path: string;
			}
		>;
		const sections = document.querySelectorAll('section');
		const navLinks = document.querySelectorAll('nav a');
		const headerFileName = document.getElementById('header-file-name');
		const headerPathName = document.getElementById('header-path-name');
		const { scrollHeight, clientHeight } = document.documentElement;

		const sectionIDs: sectionIDRecords = {
			about: { name: 'about.html', path: 'src/routes/about.html' },
			experience: { name: 'experience.html', path: 'src/routes/experience.html' },
			'highlighted-projects': {
				name: 'highlighted-projects.html',
				path: 'src/routes/highlighted-projects.html'
			}
		};

		const isSectionID = function (id: string): id is sectionID {
			return id in sectionIDs;
		};

		window.onscroll = () => {
			let currentSectionID: sectionID;
			if (scrollY <= 86) {
				currentSectionID = 'about' as sectionID;
			} else if (scrollY + clientHeight >= scrollHeight) {
				currentSectionID = 'highlighted-projects' as sectionID;
			} else {
				const currentSection = [...sections]
					.reverse()
					.find((section) => scrollY >= section.offsetTop - 86);
				currentSectionID = currentSection?.id as sectionID;
			}

			navLinks.forEach((link) => {
				link.classList.toggle('active', link.classList.contains(currentSectionID));
			});

			if (isSectionID(currentSectionID) && headerFileName && headerPathName) {
				headerFileName.textContent = sectionIDs[currentSectionID].name;
				headerPathName.textContent = sectionIDs[currentSectionID].path;
			}
		};
	}
</script>

<main class="main-container">
	<section id="about" class="about-container">
		<h1>ABOUT</h1>
		<div class="greeting-container">
			<h2>
				Jaewoon Im, full-stack developer, <br />
				experience with frontend and backend.
			</h2>
			<div>
				<span class="social-links-container">
					<a href="https://www.linkedin.com/in/jwoon/" target="_blank">
						<svelte:component this={linkedInIcon} />
					</a>
					<a href="https://www.instagram.com/jaewoon_im/" target="_blank">
						<svelte:component this={instagramIcon} />
					</a>
				</span>
				<div>
					<Button />
				</div>
			</div>
		</div>
		<div class="introduction-container">
			<pre>
			5+ years of experience as a software engineer, skilled in working independently and as part of a team on projects. Experience collaborating with some of Asia’s largest companies.
			Currently living in Copenhagen with my Danish girlfriend, looking for new career opportunities.
			</pre>
		</div>
	</section>
	<section id="experience" class="experience-container">
		<h1>EXPERIENCE</h1>
		<div class="job-container">
			<div class="job-period-container">
				<p>Oct 2021 - Oct 2023</p>
			</div>
			<div class="job-description-container">
				<a href="https://www.ryencatchers.com/" target="_blank">
					<span>
						<span><svelte:component this={linkIcon} /></span>
						<p class="job-position-company">Backend Engineer · Rye&Catchers</p>
					</span>
				</a>
				<div class="job-location-container">
					<p>Seoul, South Korea</p>
				</div>
				<div class="job-summary-container">
					<p>
						Full-stack Engineer with expertise in Java, Python, and TypeScript, specializing in
						building scalable web applications and data platforms with a proven ability to deliver
						complex projects. Successful track record of collaborating with cross-functional teams
						to develop and deploy robust solutions for major East Asian corporations.
					</p>
				</div>
				<div class="job-skill-container">
					{#each skills[0] as skill}
						<Badge {skill} />
					{/each}
				</div>
			</div>
		</div>
		<div class="job-container">
			<div class="job-period-container">
				<p>Nov 2017 - Nov 2020</p>
			</div>
			<div class="job-description-container">
				<a href="https://www.jestais.com/" target="_blank">
					<span>
						<span><svelte:component this={linkIcon} /></span>
						<p class="job-position-company">Fullstack Developer · Jesta I.S</p>
					</span>
				</a>
				<div class="job-location-container">
					<p>Montreal, Canada</p>
				</div>
				<div class="job-summary-container">
					<p>
						Developed web applications using Java and JavaScript. Proficient in building,
						maintaining, and improving web applications through code development, review, and
						testing. Demonstrated ability to collaborate effectively in a team environment, followed
						best practices for code quality and project management. Strong problem-solving skills
						with a focus on delivering stable and efficient applications.
					</p>
				</div>
				<div class="job-skill-container">
					{#each skills[1] as skill}
						<Badge {skill} />
					{/each}
				</div>
			</div>
		</div>
	</section>
	<section id="highlighted-projects" class="highlighted-projects">
		<h1>HIGHLIGHTED PROJECTS</h1>
		<div class="project-container">
			<a href="https://line.me/en/" target="_blank">
				<span>
					<span><svelte:component this={linkIcon} /></span>
					<p class="project-name">Feature Store · Line</p>
				</span>
			</a>
			<p class="project-description">
				A centralized data store using Java (Spring Boot), MySQL, Git, Docker, Kubernetes, and Naver
				Cloud Platform (A Korean AWS), providing data scientists with fast access to data for
				personalized advertising for Line - Japan's largest communication platform.
			</p>
		</div>
		<div class="project-container">
			<a href="https://product.kt.com/wDic/productDetail.do?ItemCode=1163" target="_blank">
				<span>
					<span><svelte:component this={linkIcon} /></span>
					<p class="project-name">Content classification AI for streaming platform· KT</p>
				</span>
			</a>
			<p class="project-description">
				A user-friendly frontend and backend control panel web application in Python (Django) and
				TypeScript (Vue.js) for the Korean streaming platform Genie TV owned by KT - the second
				largest telecommunications company in South Korea
			</p>
		</div>
	</section>
</main>

<style>
	.main-container {
		display: flex;
		flex-direction: column;
		justify-content: center;
		width: 100%;
	}

	section {
		padding: 24px;
	}

	.about-container {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		gap: 32px;
	}

	.greeting-container {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		flex-wrap: wrap;
		gap: 24px;
	}

	.greeting-container div {
		display: flex;
		flex-wrap: wrap;
	}

	.social-links-container {
		display: flex;
		align-items: center;
		margin-right: 12px;
	}

	.social-links-container a {
		margin-right: 12px;
	}

	.about-container div div {
		align-items: center;
	}

	.introduction-container pre {
		text-align: left;
		white-space: pre-line;
		color: var(--color-grey);
	}

	.experience-container {
		display: flex;
		flex-direction: column;
		gap: 32px;
	}

	.job-container {
		display: flex;
		flex-direction: row;
		width: 100%;
	}

	@media screen and (max-width: 600px) {
		.job-container {
			flex-direction: column;
			gap: 12px;
		}
	}

	.job-period-container {
		min-width: 200px;
	}

	.job-position-company {
		font-weight: 600;
	}

	.job-description-container {
		display: flex;
		flex-direction: column;
		gap: 8px;
	}

	.job-description-container a span {
		display: flex;
		flex-direction: row;
		gap: 6px;
	}

	.job-period-container p,
	.job-location-container p,
	.job-summary-container p {
		color: var(--color-grey);
		font-weight: 200;
	}

	.job-summary-container {
		display: flex;
		flex-direction: column;
		width: 100%;
	}

	.job-skill-container {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		gap: 14px;
		margin: 12px 0 12px 0;
	}

	.highlighted-projects {
		display: flex;
		flex-direction: column;
		gap: 32px;
	}

	.project-container {
		display: flex;
		flex-direction: column;
		gap: 12px;
	}

	.project-container a span {
		display: flex;
		flex-direction: row;
		gap: 6px;
	}

	.project-name {
		font-weight: 600;
	}

	.project-description {
		color: var(--color-grey);
		font-weight: 200;
	}
</style>
