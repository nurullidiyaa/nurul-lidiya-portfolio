<script setup>
import Navigation from '../components/Navigation.vue'
import Hero from '../components/Hero.vue'
import About from '../components/About.vue'
import Projects from '../components/Projects.vue'
import Skills from '../components/Skills.vue'
import Contact from '../components/Contact.vue'
import Footer from '../components/Footer.vue'
import BackToTop from '../components/BackToTop.vue'
</script>

<template>
  <div class="home-page">
    <Navigation />
    <Hero />
    <About />
    <Projects />
    <Skills />
    <Contact />
    <Footer />
    <BackToTop />
  </div>
</template>

<style scoped>
.home-page {
  width: 100%;
  min-height: 100vh;
  background-color: #121212;
  overflow-x: hidden;
}
</style>