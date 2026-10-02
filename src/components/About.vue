<template>
  <section ref="aboutRef" id="about" class="about">
    <div class="container">

      <!-- TITLE -->
      <h2 class="section-title" :class="{ animate: isVisible }">
        About Me
      </h2>

      <!-- INTRO -->
      <div class="about-top" :class="{ animate: isVisible }">
        <div class="about-intro">

          <!-- DESKTOP INTRO -->
          <div class="desktop-intro">
            <p class="lead">
              Computer Science (Multimedia Computing) graduate with hands-on
              experience in frontend development, responsive web design and
              website deployment. I enjoy building clean, practical interfaces
              that are easy to use and work well across devices.
            </p>

            <p>
              During my internship, I developed and maintained company websites
              while gaining experience in UI improvements, testing and
              troubleshooting. I’m currently looking for a junior frontend or
              web development role where I can continue building my skills and
              contribute to real-world projects.
            </p>
          </div>

          <!-- MOBILE INTRO -->
          <p class="mobile-intro">
            Computer Science graduate with hands-on experience in frontend development,
            responsive web design and website deployment. I enjoy building clean,
            practical interfaces that are easy to use and work well across devices.
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
          <span class="stat-label">Placements</span>
        </div>

        <div class="stat-item">
          <span class="stat-number">Available</span>
          <span class="stat-label">Now</span>
        </div>
      </div>

      <!-- HIGHLIGHTS & EXPERIENCE -->
      <div class="highlights-grid" :class="{ animate: isVisible }">
        <div class="highlight-card">
          <h4>Academic & Innovation Highlights</h4>
          <ul>
            <li>Gold Award — V-PRIDE 2025</li>
            <li>Dean’s List — 2 semesters</li>
          </ul>
        </div>

        <div class="highlight-card">
          <h4>Technical & Professional Highlights</h4>
          <ul>
            <li>Developed and deployed responsive websites</li>
            <li>Performed UI testing and issue identification</li>
            <li>Implemented content and design updates</li>
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
    ([entry]) => {
      if (entry.isIntersecting) {
        isVisible.value = true
      }
    },
    { threshold: 0.2 }
  )

  if (aboutRef.value) {
    observer.observe(aboutRef.value)
  }
})
</script>

<style scoped>
/* =========================
   ABOUT SECTION
========================= */

.about {
  position: relative;
  padding: 100px 2rem;
  background:
    radial-gradient(
      700px 220px at top center,
      rgba(0, 188, 212, 0.06),
      transparent 70%
    ),
    var(--color-bg, #121212);
}

.about::before {
  content: '';
  position: absolute;
  top: 0;
  left: 10%;
  right: 10%;
  height: 1px;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(0, 188, 212, 0.22),
    transparent
  );
}

.container {
  width: 100%;
  max-width: 1000px;
  margin: 0 auto;
}


/* =========================
   SECTION TITLE
========================= */

.section-title {
  margin: 0 0 3rem;
  font-size: 2.5rem;
  line-height: 1.2;
  font-weight: 700;
  text-align: center;
  color: var(--color-text, #f5f5f5);
  opacity: 0;
  transform: translateY(20px);
  transition: 0.8s ease;
}

.section-title.animate {
  opacity: 1;
  transform: translateY(0);
}


/* =========================
   INTRO
========================= */

.about-top {
  display: flex;
  justify-content: center;
  margin-bottom: 2.5rem;
  opacity: 0;
  transform: translateY(30px);
  transition: 0.8s ease 0.1s;
}

.about-top.animate {
  opacity: 1;
  transform: translateY(0);
}

.about-intro {
  width: 100%;
  max-width: 850px;
}

.about-intro .lead {
  margin: 0 0 1.1rem;
  font-size: 1.08rem;
  line-height: 1.75;
  font-weight: 400;
  color: var(--color-text, #f5f5f5);
}

.about-intro p {
  margin: 0;
  font-size: 1rem;
  line-height: 1.75;
  color: var(--color-muted, #aaa);
}

.mobile-intro {
  display: none;
}


/* =========================
   STATS
========================= */

.stats-row {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  margin-bottom: 2.5rem;
  opacity: 0;
  transform: translateY(30px);
  transition: 0.8s ease 0.2s;
}

.stats-row.animate {
  opacity: 1;
  transform: translateY(0);
}

.stat-item {
  min-height: 120px;
  padding: 1.2rem 1rem;
  background: var(
    --color-card-bg,
    rgba(255, 255, 255, 0.03)
  );
  border: 1px solid rgba(255, 255, 255, 0.07);
  border-radius: 12px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.stat-number {
  margin-bottom: 0.25rem;
  font-size: 1.8rem;
  line-height: 1.2;
  font-weight: 700;
  color: var(--color-accent, #00bcd4);
}

.stat-label {
  font-size: 0.82rem;
  line-height: 1.3;
  color: var(--color-muted, #aaa);
  font-weight: 500;
}


/* =========================
   HIGHLIGHTS
========================= */

.highlights-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  opacity: 0;
  transform: translateY(30px);
  transition: 0.8s ease 0.3s;
}

.highlights-grid.animate {
  opacity: 1;
  transform: translateY(0);
}

.highlight-card {
  padding: 1.4rem;
  background: var(
    --color-card-bg,
    rgba(255, 255, 255, 0.03)
  );
  border: 1px solid rgba(255, 255, 255, 0.07);
  border-left: 3px solid var(--color-accent, #00bcd4);
  border-radius: 12px;
}

.highlight-card h4 {
  margin: 0 0 0.9rem;
  font-size: 1rem;
  line-height: 1.4;
  font-weight: 600;
  color: var(--color-accent, #00bcd4);
}

.highlight-card ul {
  margin: 0;
  padding-left: 1.1rem;
}

.highlight-card li {
  margin-bottom: 0.5rem;
  font-size: 0.9rem;
  line-height: 1.55;
  color: var(--color-text, #f5f5f5);
}

.highlight-card li:last-child {
  margin-bottom: 0;
}


/* =========================
   TABLET
========================= */

@media (max-width: 992px) {
  .about {
    padding: 90px 1.5rem;
  }

  .stats-row {
    grid-template-columns: repeat(3, 1fr);
  }
}


/* =========================
   MOBILE
========================= */

@media (max-width: 600px) {
  .about {
    padding: 65px 1rem 70px;
    border-top: 1px solid rgba(0, 188, 212, 0.16);
  }

  .container {
    max-width: 100%;
  }

  /* TITLE */
  .section-title {
    margin-bottom: 1.5rem;
    font-size: 1.85rem;
    line-height: 1.2;
  }

  /* INTRO */
  .desktop-intro {
    display: none;
  }

  .mobile-intro {
    display: block;
    margin: 0;
    font-size: 0.9rem;
    line-height: 1.65;
    color: var(--color-muted, #aaa);
  }

  .about-top {
    margin-bottom: 1.8rem;
  }

  /* STATS */
  .stats-row {
    gap: 0.55rem;
    margin-bottom: 0;
    grid-template-columns: repeat(3, 1fr);
  }

  .stat-item {
    min-height: 84px;
    padding: 0.7rem 0.35rem;
    border-radius: 10px;
  }

  .stat-number {
    margin-bottom: 0.2rem;
    font-size: 1.2rem;
  }

  .stat-label {
    font-size: 0.66rem;
    line-height: 1.25;
  }

  /* HIDE HIGHLIGHTS ON MOBILE */
  .highlights-grid {
    display: none;
  }
}


/* =========================
   VERY SMALL PHONES
========================= */

@media (max-width: 360px) {
  .about {
    padding: 55px 0.85rem 65px;
  }

  .section-title {
    font-size: 1.7rem;
  }

  .mobile-intro {
    font-size: 0.86rem;
    line-height: 1.6;
  }

  .stat-item {
    min-height: 80px;
  }

  .stat-number {
    font-size: 1.05rem;
  }

  .stat-label {
    font-size: 0.61rem;
  }
}
</style>