<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }">
    <div class="nav-container">
      <div class="logo">
        <a href="#home" @click="handleNavClick">
          <span class="logo-badge">NL</span>
          <span class="logo-name">Nurul Lidiya</span>
        </a>
      </div>

      <!-- NAV MENU -->
      <ul class="nav-menu" :class="{ active: menuOpen }">
        <li><a href="#about" @click="handleNavClick">About</a></li>
        <li><a href="#projects" @click="handleNavClick">Projects</a></li>
        <li><a href="#skills" @click="handleNavClick">Skills</a></li>
        <li><a href="#contact" @click="handleNavClick">Contact</a></li>
      </ul>

      <!-- HAMBURGER BUTTON (MOBILE) -->
      <button 
        class="menu-toggle" 
        @click="toggleMenu" 
        :aria-label="menuOpen ? 'Close menu' : 'Open menu'"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const menuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value
}

const closeMenu = () => {
  menuOpen.value = false
}

const handleNavClick = (e) => {
  e.preventDefault()
  const targetId = e.currentTarget.getAttribute('href')
  
  if (targetId === '#home') {
    window.scrollTo({
      top: 0,
      behavior: 'smooth'
    })
  } else if (targetId && targetId.startsWith('#')) {
    const targetElement = document.querySelector(targetId)
    if (targetElement) {
      const offsetTop = targetElement.offsetTop - 80
      window.scrollTo({
        top: offsetTop,
        behavior: 'smooth'
      })
    }
  }
  closeMenu()
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: rgba(18, 18, 18, 0.85);
  backdrop-filter: blur(12px);
  transition: all 0.3s ease;
  padding: 1.2rem 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.navbar.scrolled {
  padding: 0.8rem 0;
  background: rgba(18, 18, 18, 0.95);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* LOGO STYLING */
.logo a {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  text-decoration: none;
  cursor: pointer;
}

.logo-badge {
  background: var(--color-accent, #00bcd4);
  color: #121212;
  font-weight: 800;
  font-size: 0.95rem;
  padding: 0.3rem 0.6rem;
  border-radius: 8px;
  letter-spacing: 0.5px;
}

.logo-name {
  font-size: 1.2rem;
  font-weight: 700;
  color: #f5f5f5;
  letter-spacing: -0.3px;
}

/* NAV MENU STYLING */
.nav-menu {
  display: flex;
  align-items: center;
  list-style: none;
  gap: 2rem;
  margin: 0;
  padding: 0;
}

.nav-menu a {
  color: rgba(245, 245, 245, 0.8);
  text-decoration: none;
  font-weight: 500;
  font-size: 0.95rem;
  transition: color 0.3s ease;
  position: relative;
}

.nav-menu a:hover {
  color: var(--color-accent, #00bcd4);
}

/* HAMBURGER TOGGLE */
.menu-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 5px;
}

.menu-toggle span {
  width: 25px;
  height: 2px;
  background: #f5f5f5;
  border-radius: 2px;
  transition: all 0.3s ease;
}

/* MOBILE RESPONSIVE */
@media (max-width: 868px) {
  .menu-toggle {
    display: flex;
  }

  .nav-menu {
    position: fixed;
    top: 70px;
    left: -100%;
    flex-direction: column;
    background: #181818;
    width: 100%;
    text-align: center;
    transition: left 0.3s ease;
    padding: 2.5rem 0;
    gap: 1.5rem;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  }

  .nav-menu.active {
    left: 0;
  }

  .nav-menu a {
    font-size: 1.1rem;
  }
}
</style>