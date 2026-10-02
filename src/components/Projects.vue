<template>
  <section id="projects" class="projects">
    <div class="container">
      <h2 class="section-title">My Projects</h2>

      <p class="section-subtitle">
        A selection of commercial internship projects and personal technical work showcasing real-world application.
      </p>

      <div class="projects-grid">
        <div v-for="project in projects" :key="project.id" class="project-card">
          <div class="project-image">
            <img :src="project.image" :alt="project.title" />
          </div>

          <div class="project-content">
            <div class="project-info">
              <span class="project-role">{{ project.role }}</span>

              <h3 class="project-title">{{ project.title }}</h3>

              <div class="tech-stack">
                <span v-for="tech in project.techStack" :key="tech" class="tech-badge">
                  {{ tech }}
                </span>
              </div>

              <p class="project-description">{{ project.description }}</p>
            </div>

            <div class="project-links">
              <a
                v-if="project.links.external"
                :href="project.links.external"
                target="_blank"
                rel="noopener noreferrer"
                class="btn btn-primary"
              >
                {{ project.links.externalLabel }}
              </a>

              <a
                v-if="project.links.internal"
                :href="project.links.internal"
                target="_blank"
                rel="noopener noreferrer"
                class="btn btn-secondary"
              >
                {{ project.links.internalLabel }}
              </a>

              <a
                v-else-if="project.links.github"
                :href="project.links.github"
                target="_blank"
                rel="noopener noreferrer"
                class="btn btn-secondary"
              >
                GitHub
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const projects = [
  {
    id: 1,
    title: 'Fine Ways Travel Website',
    role: 'Frontend Developer Intern',
    techStack: ['HTML', 'CSS', 'JavaScript', 'Domain/DNS Setup'],
    description: 'Developed and deployed a responsive travel company website. Handled UI implementation, deployment, domain configuration and basic SEO.',
    image: '/fineway.jpg',
    links: {
      external: 'https://www.finewaystravel.com.my/',
      externalLabel: 'Live Website',
      internal: 'https://github.com/nurullidiyaa/fine-ways-website-case-study',
      internalLabel: 'Case Study'
    }
  },
  {
    id: 2,
    title: 'Fine Cafe Website',
    role: 'Frontend Developer Intern',
    techStack: ['Next.js', 'React', 'Tailwind CSS'],
    description: 'Completed responsive café website using Next.js, React and Tailwind CSS with modern UI.',
    image: '/finecafe.jpg',
    links: {
      external: 'https://remarkable-biscochitos-9fa1c5.netlify.app/',
      externalLabel: 'Live Preview',
      internal: 'https://github.com/nurullidiyaa/fine-cafe-website-case-study',
      internalLabel: 'Case Study'
    }
  },
  {
    id: 3,
    title: 'Personal Developer Portfolio',
    role: 'Personal Project',
    techStack: ['Vue 3', 'Vite', 'Vue Router'],
    description: 'Personal developer portfolio built with Vue 3 and Vite, featuring reusable components, Vue Router navigation and responsive layouts.',
    image: '/portfolio.jpg',
    links: {
      external: 'https://nurul-lidiya-portfolio.vercel.app/',
      externalLabel: 'Live Demo',
      internal: 'https://github.com/nurullidiyaa/nurul-lidiya-portfolio',
      internalLabel: 'GitHub'
    }
  }
]
</script>

<style scoped>
.projects {
  position: relative;
  background:
    radial-gradient(
      700px 220px at top center,
      rgba(0, 188, 212, 0.035),
      transparent 70%
    ),
    #121212;
  padding: 100px 2rem;
  color: #f5f5f5;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-title {
  text-align: center;
  font-size: 3rem;
  font-weight: 700;
  color: var(--color-accent);
  margin-bottom: 0.5rem;
}

.section-subtitle {
  max-width: 720px;
  margin: 0 auto 3.5rem;
  text-align: center;
  color: rgba(245, 245, 245, 0.7);
  font-size: 1.1rem;
  line-height: 1.6;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.project-card {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 16px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  transition: all 0.3s ease;
}

.project-card:hover {
  transform: translateY(-6px);
  border-color: var(--color-accent);
  box-shadow: 0 12px 30px rgba(0, 188, 212, 0.15);
}

.project-image {
  width: 100%;
  height: 200px;
  background: #1a1a1a;
  overflow: hidden;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.project-card:hover .project-image img {
  transform: scale(1.05);
}

.project-content {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  flex-grow: 1;
}

.project-role {
  font-size: 0.8rem;
  font-weight: 600;
  text-transform: uppercase;
  color: rgba(245, 245, 245, 0.5);
  letter-spacing: 0.5px;
  display: block;
  margin-bottom: 0.2rem;
}

.project-title {
  font-size: 1.35rem;
  font-weight: 600;
  color: var(--color-accent);
  margin-bottom: 0.4rem;
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  margin-bottom: 1rem;
}

.tech-badge {
  background: rgba(0, 188, 212, 0.1);
  color: var(--color-accent);
  border: 1px solid rgba(0, 188, 212, 0.2);
  font-size: 0.75rem;
  padding: 0.2rem 0.5rem;
  border-radius: 4px;
  font-weight: 500;
}

.project-description {
  color: rgba(245, 245, 245, 0.7);
  font-size: 0.95rem;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.project-links {
  display: flex;
  gap: 0.8rem;
}

.btn {
  flex: 1;
  padding: 0.65rem 1.2rem;
  border-radius: 8px;
  font-weight: 500;
  font-size: 0.9rem;
  text-decoration: none;
  transition: all 0.3s ease;
  text-align: center;
}

.btn-primary {
  background: var(--color-accent);
  color: #121212;
}

.btn-primary:hover {
  opacity: 0.9;
  transform: translateY(-2px);
}

.btn-secondary {
  background: transparent;
  color: #f5f5f5;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.btn-secondary:hover {
  background: rgba(255, 255, 255, 0.08);
  border-color: #f5f5f5;
  transform: translateY(-2px);
}

@media (max-width: 600px) {
  .projects {
    padding: 65px 0.9rem;
  }

  .section-title {
    font-size: 1.8rem;
    margin-bottom: 0.5rem;
  }

  .section-subtitle {
    max-width: 310px;
    margin: 0 auto 1.7rem;
    font-size: 0.82rem;
    line-height: 1.55;
  }

  .projects-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .project-card {
    border-radius: 11px;
  }

  .project-card:hover {
    transform: none;
    border-color: rgba(255, 255, 255, 0.08);
    box-shadow: none;
  }

  .project-card:active {
    transform: translateY(-2px) scale(0.99);
    border-color: rgba(0, 188, 212, 0.4);
    box-shadow: 0 8px 20px rgba(0, 188, 212, 0.12);
  }

  .project-image {
    height: 145px;
  }

  .project-card:hover .project-image img {
    transform: none;
  }

  .project-card:active .project-image img {
    transform: scale(1.01);
  }

  .project-content {
    padding: 0.95rem;
  }

  .project-role {
    font-size: 0.62rem;
    letter-spacing: 0.45px;
    margin-bottom: 0.2rem;
  }

  .project-title {
    font-size: 1rem;
    line-height: 1.3;
    margin-bottom: 0.55rem;
  }

  .tech-stack {
    gap: 0.3rem;
    margin-bottom: 0.7rem;
  }

  .tech-badge {
    font-size: 0.6rem;
    padding: 0.18rem 0.4rem;
    border-radius: 4px;
  }

  .project-description {
    font-size: 0.76rem;
    line-height: 1.55;
    margin-bottom: 0.9rem;
  }

  .project-links {
    gap: 0.45rem;
  }

  .btn {
    padding: 0.52rem 0.55rem;
    border-radius: 7px;
    font-size: 0.72rem;
  }
}

@media (max-width: 360px) {
  .projects {
    padding: 55px 0.8rem;
  }

  .section-title {
    font-size: 1.7rem;
  }

  .section-subtitle {
    font-size: 0.78rem;
    max-width: 290px;
  }

  .project-image {
    height: 130px;
  }

  .project-content {
    padding: 0.85rem;
  }

  .project-description {
    font-size: 0.72rem;
  }

  .btn {
    font-size: 0.68rem;
    padding: 0.5rem 0.45rem;
  }
}
</style>