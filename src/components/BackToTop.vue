<template>
  <button
    v-if="isVisible"
    class="back-to-top"
    @click="scrollToTop"
    aria-label="Back to top"
  >
    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M12 19V5M12 5L5 12M12 5L19 12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  </button>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isVisible = ref(false)

const handleScroll = () => {
  isVisible.value = window.scrollY > 300
}

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.back-to-top {
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: var(--color-accent); 
  border: none;
  color: #121212; 
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 20px rgba(0, 188, 212, 0.4);
  transition: all 0.3s ease;
  z-index: 999;
}

.back-to-top:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 188, 212, 0.6);
}

.back-to-top:active {
  transform: translateY(-2px);
}

@keyframes fadeInUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .back-to-top {
    bottom: 1.5rem;
    right: 1.5rem;
    width: 45px;
    height: 45px;
  }
}

:global(.light-theme) .back-to-top {
  box-shadow: 0 4px 20px rgba(100, 108, 255, 0.3);
}

:global(.light-theme) .back-to-top:hover {
  box-shadow: 0 8px 30px rgba(100, 108, 255, 0.5);
}
</style>

