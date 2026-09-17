<template>
  <section id="skills" class="skills">
    <div class="container">
      <h2 class="section-title">Technical Skills</h2>
      <p class="section-subtitle">
        Core technologies and workflows I use to build responsive, user-focused web experiences and applications.
      </p>

      <div class="skills-categories">
        <div v-for="category in skillCategories" :key="category.title" class="category-card">
          <h3 class="category-title">{{ category.title }}</h3>
          <div class="skills-tags">
            <div v-for="skill in category.items" :key="skill.name" class="skill-tag">
              <img 
                v-if="skill.icon" 
                :src="skill.icon" 
                :alt="skill.name" 
                class="skill-icon" 
              />
              <span class="skill-badge-dot" v-else></span>
              <span>{{ skill.name }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const skillCategories = [
  {
    title: 'Frontend Development',
    items: [
      { name: 'HTML5', icon: '/html.png' },
      { name: 'CSS3', icon: '/css.png' },
      { name: 'JavaScript', icon: '/js.png' },
      { name: 'React', icon: '/react.png' },
      { name: 'Next.js', icon: '/react.png' },
      { name: 'Vue.js', icon: '/vue.png' }
    ]
  },
  {
    title: 'Backend & Database',
    items: [
      { name: 'PHP', icon: '/PHP.png' },
      { name: 'MySQL', icon: '/mysql.png' }
    ]
  },
  {
    title: 'Tools & Workflows',
    items: [
      { name: 'Responsive Web Design', icon: null },
      { name: 'Domain & DNS Setup', icon: null },
      { name: 'Basic SEO', icon: null }
    ]
  }
]
</script>

<style scoped>
.skills {
  padding: 120px 2rem;
  background:
    radial-gradient(
      700px 220px at top center,
      rgba(0, 188, 212, 0.08),
      transparent 70%
    ),
    var(--color-bg, #121212);
  color: #f5f5f5;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}

.section-title {
  font-size: 2.8rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 0.8rem;
  color: var(--color-text, #f5f5f5);
}

.section-subtitle {
  text-align: center;
  color: var(--color-muted, #aaa);
  font-size: 1.05rem;
  line-height: 1.7;
  max-width: 750px;
  margin: 0 auto 3.5rem;
}

/* CATEGORIES GRID */
.skills-categories {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
}

/* CATEGORY CARD */
.category-card {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.08);
  padding: 2rem;
  border-radius: 16px;
  transition: all 0.3s ease;
}

.category-card:hover {
  border-color: rgba(0, 188, 212, 0.3);
  box-shadow: 0 10px 30px rgba(0, 188, 212, 0.1);
}

.category-title {
  font-size: 1.25rem;
  color: var(--color-accent, #00bcd4);
  margin-bottom: 1.25rem;
  font-weight: 600;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  padding-bottom: 0.6rem;
}

/* SKILLS TAGS / BADGES */
.skills-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.8rem;
}

.skill-tag {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  background: rgba(255, 255, 255, 0.04);
  padding: 0.6rem 1rem;
  border-radius: 10px;
  font-size: 0.92rem;
  color: #f5f5f5;
  border: 1px solid rgba(255, 255, 255, 0.06);
  transition: all 0.25s ease;
}

.skill-tag:hover {
  background: rgba(0, 188, 212, 0.1);
  border-color: var(--color-accent, #00bcd4);
  transform: translateY(-2px);
}

.skill-icon {
  width: 22px;
  height: 22px;
  object-fit: contain;
}

.skill-badge-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--color-accent, #00bcd4);
  display: inline-block;
}

/* RESPONSIVE */
@media (max-width: 768px) {
  .skills-categories {
    grid-template-columns: 1fr;
  }
}
</style>