<template>
  <section id="contact" class="contact">
    <div class="container">
      <h2 class="section-title">Let's Connect</h2>
      <p class="intro">
        I'm currently open to junior frontend and web development opportunities. Feel free to reach out directly or send a message below.
      </p>

      <div class="contact-split">
        <!-- LEFT: DIRECT CHANNELS -->
        <div class="contact-info">
          <h3>Get In Touch Directly</h3>
          <p class="info-desc">
            Prefer direct channels? You can email me directly or start a chat via WhatsApp for a quick discussion.
          </p>

          <div class="direct-buttons">
            <a href="mailto:nurullidiyaa@gmail.com" class="direct-btn email-btn">
              <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="btn-icon">
                <rect width="20" height="16" x="2" y="4" rx="2"/>
                <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/>
              </svg>
              <span>Email Me</span>
            </a>

            <a href="https://wa.link/og9qr6" target="_blank" rel="noopener noreferrer" class="direct-btn wa-btn">
              <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="btn-icon">
                <path d="M7.9 20A9 9 0 1 0 4 16.1L2 22Z"/>
              </svg>
              <span>WhatsApp Me</span>
            </a>
          </div>

          <div class="social-list">
            <p>Connect on professional networks:</p>
            <div class="links">
              <a href="https://www.linkedin.com/in/nurul-lidiya/" target="_blank" rel="noopener noreferrer">LinkedIn ↗</a>
              <a href="https://github.com/nurullidiyaa" target="_blank" rel="noopener noreferrer">GitHub ↗</a>
            </div>
          </div>
        </div>

        <!-- RIGHT: CONTACT FORM -->
        <form class="contact-form" @submit.prevent="handleSubmit">
          <div class="form-group">
            <label for="name">Name</label>
            <input
              type="text"
              id="name"
              v-model="form.name"
              placeholder="Your name"
              required
            />
          </div>

          <div class="form-group">
            <label for="email">Email</label>
            <input
              type="email"
              id="email"
              v-model="form.email"
              placeholder="you@example.com"
              required
            />
          </div>

          <div class="form-group">
            <label for="subject">Subject</label>
            <input
              type="text"
              id="subject"
              v-model="form.subject"
              placeholder="Project / Job Opportunity"
              required
            />
          </div>

          <div class="form-group">
            <label for="message">Message</label>
            <textarea
              id="message"
              rows="4"
              v-model="form.message"
              placeholder="Tell me more about it..."
              required
            ></textarea>
          </div>

          <button type="submit" :disabled="loading">
            {{ loading ? 'Sending...' : 'Send Message' }}
          </button>

          <p v-if="successMessage" class="success-msg">
            {{ successMessage }}
          </p>
          <p v-if="errorMessage" class="error-msg">
            {{ errorMessage }}
          </p>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref, onMounted } from 'vue'
import emailjs from '@emailjs/browser'

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const loading = ref(false)
const successMessage = ref('')
const errorMessage = ref('')

onMounted(() => {
  const publicKey = import.meta.env.VITE_EMAILJS_PUBLIC_KEY
  if (publicKey) {
    emailjs.init(publicKey)
  }
})

const handleSubmit = async () => {
  loading.value = true
  successMessage.value = ''
  errorMessage.value = ''

  const serviceID = import.meta.env.VITE_EMAILJS_SERVICE_ID
  const templateID = import.meta.env.VITE_EMAILJS_TEMPLATE_ID
  const publicKey = import.meta.env.VITE_EMAILJS_PUBLIC_KEY

  if (!serviceID || !templateID || !publicKey) {
    console.error('EmailJS env variables missing')
    errorMessage.value = 'Configuration error. Please check environment variables.'
    loading.value = false
    return
  }

  try {
    await emailjs.send(
      serviceID,
      templateID,
      {
        name: form.name,
        email: form.email,
        subject: form.subject,
        message: form.message
      },
      publicKey
    )

    successMessage.value = 'Thank you! Your message has been sent successfully.'

    form.name = ''
    form.email = ''
    form.subject = ''
    form.message = ''
  } catch (err) {
    console.error('EmailJS Error:', err)
    errorMessage.value = err?.text || 'Oops! Something went wrong. Please try again later.'
  } finally {
    loading.value = false
  }
}
</script>

<style scoped>
.contact {
  padding: 100px 2rem;
  background: #121212;
  color: #f5f5f5;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}

.section-title {
  text-align: center;
  font-size: 2.8rem;
  font-weight: 700;
  color: var(--color-accent, #00bcd4);
  margin-bottom: 0.5rem;
}

.intro {
  text-align: center;
  color: rgba(245, 245, 245, 0.7);
  font-size: 1.1rem;
  max-width: 650px;
  margin: 0 auto 3.5rem;
  line-height: 1.6;
}

/* SPLIT LAYOUT */
.contact-split {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 3rem;
  align-items: start;
}

/* LEFT DIRECT INFO CARD */
.contact-info {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.08);
  padding: 2.5rem;
  border-radius: 20px;
  text-align: left;
}

.contact-info h3 {
  font-size: 1.4rem;
  color: #f5f5f5;
  margin-bottom: 0.8rem;
}

.info-desc {
  color: rgba(245, 245, 245, 0.7);
  font-size: 0.95rem;
  line-height: 1.6;
  margin-bottom: 2rem;
}

.direct-buttons {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 2rem;
}

.direct-btn {
  padding: 0.85rem 1.2rem;
  border-radius: 12px;
  text-decoration: none;
  font-weight: 600;
  text-align: center;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}

.email-btn {
  background: var(--color-accent, #00bcd4);
  color: #121212;
}

.email-btn:hover {
  opacity: 0.9;
  transform: translateY(-2px);
}

.wa-btn {
  background: rgba(76, 175, 80, 0.15);
  border: 1px solid rgba(76, 175, 80, 0.4);
  color: #81c784;
}

.wa-btn:hover {
  background: #4caf50;
  color: #121212;
  transform: translateY(-2px);
}

.social-list p {
  font-size: 0.88rem;
  color: rgba(245, 245, 245, 0.5);
  margin-bottom: 0.6rem;
}

.social-list .links {
  display: flex;
  gap: 1.2rem;
}

.social-list a {
  color: var(--color-accent, #00bcd4);
  text-decoration: none;
  font-size: 0.95rem;
  font-weight: 500;
  transition: color 0.2s ease;
}

.social-list a:hover {
  text-decoration: underline;
}

/* RIGHT CONTACT FORM */
.contact-form {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.08);
  padding: 2.5rem;
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}

.form-group {
  display: flex;
  flex-direction: column;
  text-align: left;
}

.form-group label {
  margin-bottom: 0.4rem;
  font-size: 0.88rem;
  color: rgba(245, 245, 245, 0.7);
}

.form-group input,
.form-group textarea {
  padding: 0.85rem 1rem;
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.12);
  background: rgba(0, 0, 0, 0.25);
  color: #f5f5f5;
  font-size: 0.95rem;
  transition: all 0.3s ease;
}

.form-group input:hover,
.form-group textarea:hover {
  border-color: rgba(255, 255, 255, 0.25);
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--color-accent, #00bcd4);
  box-shadow: 0 0 0 3px rgba(0, 188, 212, 0.15);
}

button[type='submit'] {
  margin-top: 0.5rem;
  padding: 0.85rem 1.5rem;
  border-radius: 10px;
  background: var(--color-accent, #00bcd4);
  color: #121212;
  font-weight: 600;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
}

button[type='submit']:hover:not(:disabled) {
  opacity: 0.9;
  transform: translateY(-2px);
}

button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.success-msg {
  color: #81c784;
  font-size: 0.9rem;
  text-align: center;
  margin-top: 0.5rem;
}

.error-msg {
  color: #e57373;
  font-size: 0.9rem;
  text-align: center;
  margin-top: 0.5rem;
}

/* RESPONSIVE */
@media (max-width: 868px) {
  .contact-split {
    grid-template-columns: 1fr;
  }
}
</style>