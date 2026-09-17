<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <!-- BRAND SECTION -->
        <div class="footer-section brand-section">
          <h3>Nurul Lidiya</h3>
          <p>Junior Frontend Developer</p>
          <p class="tagline">Building responsive, user-focused web experiences.</p>
        </div>

        <!-- QUICK LINKS -->
        <div class="footer-section">
          <h4>Quick Links</h4>
          <ul>
            <li><a href="#home" @click="handleNavClick">Home</a></li>
            <li><a href="#about" @click="handleNavClick">About</a></li>
            <li><a href="#projects" @click="handleNavClick">Projects</a></li>
            <li><a href="#skills" @click="handleNavClick">Skills</a></li>
            <li><a href="#contact" @click="handleNavClick">Contact</a></li>
          </ul>
        </div>

        <!-- CONNECT (SOCIAL ICONS) -->
        <div class="footer-section">
          <h4>Connect</h4>
          <div class="footer-social">
            <!-- GitHub -->
            <a 
              href="https://github.com/nurullidiyaa" 
              target="_blank" 
              rel="noopener noreferrer"
              aria-label="GitHub"
            >
              <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/>
              </svg>
            </a>

            <!-- LinkedIn -->
            <a 
              href="https://www.linkedin.com/in/nurul-lidiya/" 
              target="_blank" 
              rel="noopener noreferrer"
              aria-label="LinkedIn"
            >
              <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
              </svg>
            </a>

            <!-- Email -->
            <a 
              href="mailto:nurullidiyaa@gmail.com" 
              aria-label="Email"
            >
              <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path d="M0 3v18h24v-18h-24zm21.518 2l-9.518 6.013-9.518-6.013h19.036zm-19.518 14v-11.817l10 6.328 10-6.328v11.817h-20z"/>
              </svg>
            </a>

            <!-- WhatsApp -->
            <a 
              href="https://wa.link/og9qr6" 
              target="_blank" 
              rel="noopener noreferrer"
              aria-label="WhatsApp"
            >
              <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946.003-6.556 5.338-11.891 11.893-11.891 3.181.001 6.167 1.24 8.413 3.488 2.245 2.248 3.481 5.236 3.48 8.414-.003 6.557-5.338 11.892-11.893 11.892-1.99-.001-3.951-.5-5.688-1.448l-6.305 1.654zm6.597-3.807c1.676.995 3.276 1.591 5.392 1.592 5.448 0 9.886-4.434 9.889-9.885.002-5.462-4.415-9.89-9.881-9.892-5.452 0-9.887 4.434-9.889 9.884-.001 2.225.651 3.891 1.746 5.634l-.999 3.648 3.742-.981z"/>
              </svg>
            </a>
          </div>
        </div>
      </div>

      <!-- COPYRIGHT -->
      <div class="footer-bottom">
        <p>&copy; {{ currentYear }} Nurul Lidiya. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue'

const currentYear = computed(() => new Date().getFullYear())

const handleNavClick = (e) => {
  e.preventDefault()
  const targetId = e.target.getAttribute('href')
  if (targetId && targetId.startsWith('#')) {
    const targetElement = document.querySelector(targetId)
    if (targetElement) {
      const offsetTop = targetElement.offsetTop - 80
      window.scrollTo({
        top: offsetTop,
        behavior: 'smooth'
      })
    }
  }
}
</script>

<style scoped>
.footer {
  background: #121212;
  padding: 4rem 2rem 1.5rem;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
  color: #f5f5f5;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.footer-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 2.5rem;
  margin-bottom: 3rem;
}

.brand-section h3 {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 0.2rem;
  color: var(--color-accent, #00bcd4);
}

.brand-section p {
  font-size: 0.95rem;
  color: #f5f5f5;
  margin-bottom: 0.5rem;
}

.brand-section .tagline {
  color: rgba(245, 245, 245, 0.6);
  font-size: 0.88rem;
  line-height: 1.5;
}

.footer-section h4 {
  font-size: 1.15rem;
  font-weight: 600;
  margin-bottom: 1.2rem;
  color: #f5f5f5;
}

.footer-section ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-section ul li {
  margin-bottom: 0.6rem;
}

.footer-section ul li a {
  color: rgba(245, 245, 245, 0.65);
  text-decoration: none;
  font-size: 0.95rem;
  transition: color 0.3s ease;
}

.footer-section ul li a:hover {
  color: var(--color-accent, #00bcd4);
}

/* SOCIAL ICONS STYLING */
.footer-social {
  display: flex;
  gap: 0.8rem;
  align-items: center;
}

.footer-social a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 42px;
  height: 42px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: rgba(245, 245, 245, 0.75);
  transition: all 0.3s ease;
}

.footer-social a:hover {
  color: var(--color-accent, #00bcd4);
  border-color: var(--color-accent, #00bcd4);
  background: rgba(0, 188, 212, 0.1);
  transform: translateY(-3px);
}

/* FOOTER BOTTOM */
.footer-bottom {
  text-align: center;
  padding-top: 2rem;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
}

.footer-bottom p {
  color: rgba(245, 245, 245, 0.5);
  font-size: 0.9rem;
  margin: 0;
}
</style>