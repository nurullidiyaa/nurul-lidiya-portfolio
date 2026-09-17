<template>
  <section id="home" class="hero">
    <!-- SUBTLE AMBIENT GLOW BACKGROUND -->
    <div class="hero-glow"></div>

    <div class="hero-content">
      <!-- TEXT CONTENT -->
      <div class="hero-text" :class="{ animate: isVisible }">
        <!-- AVAILABILITY BADGE -->
        <div class="status-badge">
          <span class="status-dot"></span>
          <span>Available for opportunities</span>
        </div>

        <!-- NAME -->
        <h1 class="hero-title">
          <span class="greeting">Hi, I'm</span>
          <span class="name">Nurul Lidiya</span>
        </h1>

        <!-- STATIC ROLE -->
        <p class="hero-subtitle">
          <span class="primary-role">Junior Frontend Developer</span>
          <span class="role-divider"> · </span>
          <span class="secondary-role">Web Developer</span>
        </p>

        <!-- DESCRIPTION -->
        <p class="hero-description">
          Computer Science (Multimedia Computing) graduate with hands-on
          experience building responsive web interfaces, implementing modern
          UI and managing live web deployments.
        </p>

        <!-- CTA BUTTONS -->
        <div class="hero-buttons">
          <a
            href="#projects"
            class="btn btn-primary"
            @click.prevent="scrollToSection('#projects')"
          >
            View My Work
          </a>

          <a
            href="/Nurul_Lidiya_Resume.pdf"
            target="_blank"
            rel="noopener noreferrer"
            class="btn btn-secondary"
          >
            View Resume ↗
          </a>
        </div>

        <!-- QUICK SOCIAL LINKS -->
        <div class="hero-socials">
          <!-- GitHub -->
          <a
            href="https://github.com/nurullidiyaa"
            target="_blank"
            rel="noopener noreferrer"
            aria-label="GitHub"
          >
            <svg
              width="18"
              height="18"
              viewBox="0 0 24 24"
              fill="currentColor"
            >
              <path
                d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"
              />
            </svg>
            <span>GitHub</span>
          </a>

          <!-- LinkedIn -->
          <a
            href="https://www.linkedin.com/in/nurul-lidiya/"
            target="_blank"
            rel="noopener noreferrer"
            aria-label="LinkedIn"
          >
            <svg
              width="18"
              height="18"
              viewBox="0 0 24 24"
              fill="currentColor"
            >
              <path
                d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"
              />
            </svg>
            <span>LinkedIn</span>
          </a>

          <!-- Email -->
          <a
            href="mailto:nurullidiyaa@gmail.com"
            aria-label="Email"
          >
            <svg
              width="18"
              height="18"
              viewBox="0 0 24 24"
              fill="currentColor"
            >
              <path
                d="M0 3v18h24v-18h-24zm21.518 2l-9.518 6.013-9.518-6.013h19.036zm-19.518 14v-11.817l10 6.328 10-6.328v11.817h-20z"
              />
            </svg>
            <span>Email</span>
          </a>

          <!-- WhatsApp -->
          <a
            href="https://wa.link/og9qr6"
            target="_blank"
            rel="noopener noreferrer"
            aria-label="WhatsApp"
          >
            <svg
              width="18"
              height="18"
              viewBox="0 0 24 24"
              fill="currentColor"
            >
              <path
                d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946.003-6.556 5.338-11.891 11.893-11.891 3.181.001 6.167 1.24 8.413 3.488 2.245 2.248 3.481 5.236 3.48 8.414-.003 6.557-5.338 11.892-11.893 11.892-1.99-.001-3.951-.5-5.688-1.448l-6.305 1.654zm6.597-3.807c1.676.995 3.276 1.591 5.392 1.592 5.448 0 9.886-4.434 9.889-9.885.002-5.462-4.415-9.89-9.881-9.892-5.452 0-9.887 4.434-9.889 9.884-.001 2.225.651 3.891 1.746 5.634l-.999 3.648 3.742-.981z"
              />
            </svg>
            <span>WhatsApp</span>
          </a>
        </div>
      </div>

      <!-- PROFILE IMAGE -->
      <div class="hero-image" :class="{ animate: isVisible }">
        <div class="image-frame">
          <img
            src="/gambar.png"
            alt="Nurul Lidiya"
            class="profile-image"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isVisible = ref(false)

onMounted(() => {
  isVisible.value = true
})

const scrollToSection = (selector) => {
  const el = document.querySelector(selector)

  if (el) {
    window.scrollTo({
      top: el.offsetTop - 80,
      behavior: 'smooth'
    })
  }
}
</script>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding: 130px 2rem 4rem;
  background: #121212;
  overflow: hidden;
}

/* =========================
   AMBIENT GLOW
========================= */

.hero-glow {
  position: absolute;
  top: -100px;
  left: 10%;
  width: 600px;
  height: 600px;

  background: radial-gradient(
    circle,
    rgba(0, 188, 212, 0.12) 0%,
    rgba(99, 102, 241, 0.05) 40%,
    transparent 70%
  );

  pointer-events: none;
  z-index: 1;
}

/* =========================
   MAIN CONTENT
========================= */

.hero-content {
  position: relative;
  z-index: 2;

  width: 100%;
  max-width: 1200px;
  margin: 0 auto;

  display: grid;
  grid-template-columns: 1.25fr 0.75fr;
  gap: 3.5rem;
  align-items: center;
}

/* =========================
   STATUS BADGE
========================= */

.status-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;

  padding: 0.4rem 0.9rem;
  margin-bottom: 1.5rem;

  border-radius: 999px;

  background: rgba(76, 175, 80, 0.1);
  border: 1px solid rgba(76, 175, 80, 0.25);

  font-size: 0.85rem;
  color: #81c784;
  font-weight: 500;
}

.status-dot {
  width: 8px;
  height: 8px;

  border-radius: 50%;

  background: #4caf50;
  box-shadow: 0 0 10px #4caf50;

  animation: pulse 2s infinite;
}

@keyframes pulse {
  0% {
    transform: scale(0.95);
    box-shadow: 0 0 0 0 rgba(76, 175, 80, 0.7);
  }

  70% {
    transform: scale(1);
    box-shadow: 0 0 0 8px rgba(76, 175, 80, 0);
  }

  100% {
    transform: scale(0.95);
    box-shadow: 0 0 0 0 rgba(76, 175, 80, 0);
  }
}

/* =========================
   TEXT
========================= */

.hero-text {
  opacity: 0;
  transform: translateY(30px);

  transition:
    opacity 0.8s ease,
    transform 0.8s ease;
}

.hero-text.animate {
  opacity: 1;
  transform: translateY(0);
}

.hero-title {
  margin-bottom: 0.8rem;

  font-size: 3.8rem;
  line-height: 1.1;

  color: #f5f5f5;
}

.greeting {
  display: block;

  margin-bottom: 0.2rem;

  font-size: 1.5rem;
  font-weight: 400;

  color: #aaa;
}

.name {
  position: relative;
  display: inline-block;

  font-weight: 700;
  color: var(--color-accent, #00bcd4);
}

.name::after {
  content: '';

  display: block;

  width: 56px;
  height: 5px;

  margin-top: 0.4rem;

  border-radius: 4px;
  background: var(--color-accent, #00bcd4);
}

/* =========================
   ROLE
========================= */

.hero-subtitle {
  margin: 1.2rem 0 1.5rem;

  font-size: 1.65rem;
  line-height: 1.4;
}

.primary-role {
  color: var(--color-accent, #00bcd4);
  font-weight: 600;
}

.role-divider {
  color: rgba(245, 245, 245, 0.4);
}

.secondary-role {
  color: rgba(245, 245, 245, 0.75);
  font-weight: 500;
}

.hero-description {
  max-width: 540px;

  margin-bottom: 2rem;

  font-size: 1.1rem;
  line-height: 1.7;

  color: rgba(245, 245, 245, 0.75);
}

/* =========================
   BUTTONS
========================= */

.hero-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;

  margin-bottom: 2.2rem;
}

.btn {
  padding: 0.85rem 2rem;

  border-radius: 10px;

  font-size: 0.95rem;
  font-weight: 600;

  text-decoration: none;

  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease,
    background 0.3s ease,
    border-color 0.3s ease,
    color 0.3s ease;
}

.btn-primary {
  background: var(--color-accent, #00bcd4);
  color: #121212;
}

.btn-primary:hover {
  transform: translateY(-2px);

  box-shadow:
    0 10px 25px rgba(0, 188, 212, 0.35);
}

.btn-secondary {
  background: rgba(255, 255, 255, 0.04);

  border: 1px solid rgba(255, 255, 255, 0.2);

  color: #f5f5f5;
}

.btn-secondary:hover {
  transform: translateY(-2px);

  background: rgba(255, 255, 255, 0.08);

  border-color: var(--color-accent, #00bcd4);

  color: var(--color-accent, #00bcd4);
}

/* =========================
   SOCIAL LINKS
========================= */

.hero-socials {
  display: flex;
  align-items: center;
  flex-wrap: wrap;

  gap: 1.5rem;
}

.hero-socials a {
  display: flex;
  align-items: center;

  gap: 0.5rem;

  font-size: 0.9rem;
  font-weight: 500;

  color: rgba(245, 245, 245, 0.65);

  text-decoration: none;

  transition:
    color 0.3s ease,
    transform 0.3s ease;
}

.hero-socials a:hover {
  color: var(--color-accent, #00bcd4);

  transform: translateY(-2px);
}

/* =========================
   PROFILE IMAGE
========================= */

.hero-image {
  max-width: 280px;

  margin: 0 auto;

  opacity: 0;
  transform: translateX(30px);

  transition:
    opacity 0.8s ease 0.2s,
    transform 0.8s ease 0.2s;
}

.hero-image.animate {
  opacity: 1;
  transform: translateX(0);
}

.image-frame {
  padding: 8px;

  border-radius: 24px;

  background: rgba(0, 188, 212, 0.12);

  border: 1px solid rgba(0, 188, 212, 0.25);

  box-shadow:
    0 0 40px rgba(0, 188, 212, 0.15);
}

.profile-image {
  display: block;

  width: 100%;

  border-radius: 18px;

  background: #1e1e1e;
}

/* =========================
   RESPONSIVE
========================= */

@media (max-width: 900px) {
  .hero {
    padding-top: 110px;
  }

  .hero-content {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .hero-description {
    margin: 0 auto 2rem;
  }

  .hero-buttons {
    justify-content: center;
  }

  .hero-socials {
    justify-content: center;
  }

  .name::after {
    margin: 0.4rem auto 0;
  }

  .hero-image {
    max-width: 220px;

    order: -1;

    margin-bottom: 1.5rem;
  }
}

@media (max-width: 600px) {
  .hero {
    min-height: auto;

    padding:
      110px 1.25rem
      4rem;
  }

  .hero-title {
    font-size: 2.8rem;
  }

  .greeting {
    font-size: 1.2rem;
  }

  .hero-subtitle {
    font-size: 1.25rem;
  }

  .role-divider {
    display: none;
  }

  .secondary-role {
    display: block;
    margin-top: 0.25rem;
  }

  .hero-description {
    font-size: 1rem;
  }

  .hero-buttons {
    flex-direction: column;
  }

  .btn {
    width: 100%;
    text-align: center;
  }

  .hero-socials {
    gap: 1rem 1.25rem;
  }
}
</style>