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

              <!-- TECH STACK BADGES -->
              <div class="tech-stack">
                <span v-for="tech in project.techStack" :key="tech" class="tech-badge">
                  {{ tech }}
                </span>
              </div>

              <p class="project-description">{{ project.description }}</p>
            </div>

            <div class="project-links">
              <!-- Action Button 1 (External / Demo) -->
              <a
                v-if="project.links.external"
                :href="project.links.external"
                target="_blank"
                rel="noopener noreferrer"
                class="btn btn-primary"
              >
                {{ project.links.externalLabel }}
              </a>

              <!-- Action Button 2 (Case Study) -->
              <a
                v-if="project.links.internal"
                :href="project.links.internal"
                target="_blank"
                rel="noopener noreferrer"
                class="btn btn-secondary"
              >
                {{ project.links.internalLabel }}
              </a>

              <!-- GitHub Link-->
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
    description: 'Developed and deployed a responsive travel company website during my internship. Handled UI implementation, content updates, deployment, domain configuration and basic SEO.',
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
    description: 'Completed responsive café website using Next.js, React and Tailwind CSS with modern UI components and interactive elements.',
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
    description: 'Personal developer portfolio built with Vue 3 and Vite, featuring reusable components, Vue Router navigation, responsive layouts and interactive UI elements.',
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
  background: #121212;
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
  text-align: center;
  color: rgba(245, 245, 245, 0.7);
  font-size: 1.1rem;
  margin-bottom: 3.5rem;
}

/* GRID */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

/* CARD LAYOUT FIX */
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

/* IMAGE FIX */
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

/* CONTENT ALIGNMENT */
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

/* TECH STACK BADGES */
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

/* BUTTONS */
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
</style>