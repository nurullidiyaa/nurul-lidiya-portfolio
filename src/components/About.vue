<template>
  <section ref="aboutRef" id="about" class="about">
    <div class="container">
      <!-- TITLE -->
      <h2 class="section-title" :class="{ animate: isVisible }">About Me</h2>

      <!-- INTRO + CARD -->
      <div class="about-top" :class="{ animate: isVisible }">
        <!-- INTRO TEXT -->
        <div class="about-intro">
          <p class="lead">
            Computer Science (Multimedia Computing) graduate from Universiti Teknologi MARA with hands-on experience in frontend development, responsive web design and web-based projects. I enjoy building practical digital solutions with a focus on usability, clean interfaces and reliable functionality.
          </p>
          <p>
            During my internship at Fine Ways Travel & Tours, I developed and maintained company websites, implemented UI improvements and managed live deployments. I also gained experience in testing, troubleshooting and working through multiple revisions based on business requirements. I’m currently looking for a junior role where I can apply my technical skills while continuing to grow in a professional environment.
          </p>
        </div>
      </div>

      <!-- STATS -->
      <div class="stats-row" :class="{ animate: isVisible }">
        <div class="stat-item">
          <span class="stat-number">3.30</span>
          <span class="stat-label">CGPA</span>
        </div>
        <div class="stat-item">
          <span class="stat-number">2</span>
          <span class="stat-label">Industry Placements</span>
        </div>
        <div class="stat-item">
          <span class="stat-number">Immediate</span>
          <span class="stat-label">Availability</span>
        </div>
      </div>

      <!-- HIGHLIGHTS & EXPERIENCE -->
      <div class="highlights-grid" :class="{ animate: isVisible }">
        <div class="highlight-card">
          <h4>Academic & Innovation Highlights</h4>
          <ul>
            <li>Gold Award – V-PRIDE 2025 Innovation Showcase</li>
            <li>Dean’s List – Two consecutive semesters</li>
          </ul>
        </div>

        <div class="highlight-card">
          <h4>Technical & Professional Highlights</h4>
          <ul>
            <li>Developed and deployed responsive company websites</li>
            <li>Performed website testing, UI improvements and issue identification</li>
            <li>Worked with stakeholders to implement content and design revisions</li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isVisible = ref(false)
const aboutRef = ref(null)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => entry.isIntersecting && (isVisible.value = true),
    { threshold: 0.2 }
  )
  if (aboutRef.value) {
    observer.observe(aboutRef.value)
  }
})
</script>

<style scoped>
.about {
  padding: 120px 2rem;
  background:
    radial-gradient(
      700px 220px at top center,
      rgba(0, 188, 212, 0.08),
      transparent 70%
    ),
    var(--color-bg, #121212);
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}

/* TITLE */
.section-title {
  font-size: 2.8rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 3.5rem;
  color: var(--color-text, #f5f5f5);
  opacity: 0;
  transform: translateY(20px);
  transition: 0.8s ease;
}

.section-title.animate {
  opacity: 1;
  transform: translateY(0);
}

.about-top {
  display: flex;
  justify-content: center;
  margin-bottom: 3rem;
  opacity: 0;
  transform: translateY(30px);
  transition: 0.8s ease 0.1s;
}

.about-intro {
  width: 100%;
  max-width: 900px;
  text-align: left;
}

.about-top.animate {
  opacity: 1;
  transform: translateY(0);
}

/* INTRO */
.about-intro .lead {
  font-size: 1.18rem;
  line-height: 1.7;
  font-weight: 400;
  margin-bottom: 1.2rem;
  color: var(--color-text, #f5f5f5);
}

.about-intro p {
  font-size: 1.05rem;
  line-height: 1.7;
  margin-bottom: 1rem;
  color: var(--color-muted, #ccc);
}

/* CARD */
.about-card {
  background: linear-gradient(135deg, rgba(0, 188, 212, 0.08), rgba(0, 188, 212, 0.03));
  border-radius: 16px;
  padding: 1.8rem 1.5rem;
  text-align: center;
  border: 1px solid rgba(0, 188, 212, 0.2);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.about-card h3 {
  font-size: 1.4rem;
  font-weight: 600;
  margin-bottom: 1rem;
  color: var(--color-text, #f5f5f5);
}

.btn-contact {
  padding: 0.75rem 1.8rem;
  border-radius: 8px;
  background: var(--color-accent, #00bcd4);
  color: #121212;
  font-weight: 600;
  text-decoration: none;
  transition: all 0.3s ease;
}

.btn-contact:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(0, 188, 212, 0.3);
}

/* STATS */
.stats-row {
  display: flex;
  gap: 1.5rem;
  margin-bottom: 3rem;
  opacity: 0;
  transform: translateY(30px);
  transition: 0.8s ease 0.2s;
}

.stats-row.animate {
  opacity: 1;
  transform: translateY(0);
}

.stat-item {
  flex: 1;
  background: var(--color-card-bg, rgba(255, 255, 255, 0.03));
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 16px;
  padding: 1.5rem;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.stat-number {
  font-size: 2.2rem;
  font-weight: 700;
  color: var(--color-accent, #00bcd4);
  margin-bottom: 0.3rem;
}

.stat-label {
  font-size: 0.95rem;
  color: var(--color-muted, #aaa);
  font-weight: 500;
}

/* HIGHLIGHTS GRID */
.highlights-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
  opacity: 0;
  transform: translateY(30px);
  transition: 0.8s ease 0.3s;
}

.highlights-grid.animate {
  opacity: 1;
  transform: translateY(0);
}

.highlight-card {
  background: var(--color-card-bg, rgba(255, 255, 255, 0.03));
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-left: 4px solid var(--color-accent, #00bcd4);
  padding: 1.8rem;
  border-radius: 16px;
}

.highlight-card h4 {
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 1rem;
  color: var(--color-accent, #00bcd4);
}

.highlight-card ul {
  padding-left: 1.2rem;
  margin: 0;
}

.highlight-card li {
  margin-bottom: 0.6rem;
  font-size: 0.98rem;
  color: var(--color-text, #f5f5f5);
  line-height: 1.6;
}

/* RESPONSIVE */
@media (max-width: 992px) {
  .about-top {
    grid-template-columns: 1fr;
  }
  .stats-row {
    flex-direction: column;
  }
  .highlights-grid {
    grid-template-columns: 1fr;
  }
}
</style>