<template>
  <section id="contact" class="contact">
    <div class="contact-container">
      <div class="section-header">
        <h2 class="section-title">Let's Connect</h2>
        <p class="section-subtitle">
          I'm currently open to junior frontend and web development opportunities.
          Feel free to reach out through the form below.
        </p>
      </div>

      <form class="contact-form" @submit.prevent="sendEmail">
        <div class="form-group">
          <label for="name">Name</label>
          <input
            id="name"
            v-model="form.name"
            type="text"
            name="name"
            placeholder="Your name"
            required
          />
        </div>

        <div class="form-group">
          <label for="email">Email</label>
          <input
            id="email"
            v-model="form.email"
            type="email"
            name="email"
            placeholder="your@email.com"
            required
          />
        </div>

        <div class="form-group">
          <label for="subject">Subject</label>
          <input
            id="subject"
            v-model="form.subject"
            type="text"
            name="subject"
            placeholder="What would you like to talk about?"
            required
          />
        </div>

        <div class="form-group">
          <label for="message">Message</label>
          <textarea
            id="message"
            v-model="form.message"
            name="message"
            rows="5"
            placeholder="Write your message..."
            required
          ></textarea>
        </div>

        <button type="submit" class="submit-button" :disabled="isSending">
          {{ isSending ? 'Sending...' : 'Send Message' }}
        </button>

        <p v-if="successMessage" class="form-message success">
          {{ successMessage }}
        </p>

        <p v-if="errorMessage" class="form-message error">
          {{ errorMessage }}
        </p>
      </form>
    </div>
  </section>
</template>

<script setup>
import { onMounted, reactive, ref } from 'vue'
import emailjs from '@emailjs/browser'

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const isSending = ref(false)
const successMessage = ref('')
const errorMessage = ref('')

const serviceId = import.meta.env.VITE_EMAILJS_SERVICE_ID
const templateId = import.meta.env.VITE_EMAILJS_TEMPLATE_ID
const publicKey = import.meta.env.VITE_EMAILJS_PUBLIC_KEY

onMounted(() => {
  if (publicKey) {
    emailjs.init(publicKey)
  }
})

const sendEmail = async () => {
  if (isSending.value) return

  isSending.value = true
  successMessage.value = ''
  errorMessage.value = ''

  try {
    await emailjs.send(
      serviceId,
      templateId,
      {
        name: form.name,
        email: form.email,
        subject: form.subject,
        message: form.message
      },
      publicKey
    )

    successMessage.value = 'Message sent successfully. Thank you for reaching out!'

    form.name = ''
    form.email = ''
    form.subject = ''
    form.message = ''
  } catch (error) {
    console.error('EmailJS error:', error)
    errorMessage.value = 'Something went wrong. Please try again later.'
  } finally {
    isSending.value = false
  }
}
</script>

<style scoped>
.contact {
  padding: 100px 2rem;
  background:
    radial-gradient(
      700px 220px at top center,
      rgba(0, 188, 212, 0.035),
      transparent 70%
    ),
    #121212;
  color: #f5f5f5;
}

.contact-container {
  max-width: 760px;
  margin: 0 auto;
}

.section-header {
  text-align: center;
  margin-bottom: 2.8rem;
}

.section-title {
  margin: 0 0 0.7rem;
  font-size: 2.8rem;
  font-weight: 700;
  letter-spacing: -0.03em;
}

.section-subtitle {
  max-width: 600px;
  margin: 0 auto;
  color: rgba(245, 245, 245, 0.62);
  font-size: 1rem;
  line-height: 1.7;
}

.contact-form {
  max-width: 680px;
  margin: 0 auto;
  padding: 2rem;
  background: rgba(255, 255, 255, 0.018);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 14px;
}

.form-group {
  margin-bottom: 1.3rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  color: rgba(245, 245, 245, 0.85);
  font-size: 0.85rem;
  font-weight: 500;
}

.form-group input,
.form-group textarea {
  width: 100%;
  box-sizing: border-box;
  padding: 0.8rem 0.9rem;
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 8px;
  outline: none;
  background: rgba(255, 255, 255, 0.035);
  color: #f5f5f5;
  font-family: inherit;
  font-size: 0.85rem;
  transition:
    border-color 0.2s ease,
    background 0.2s ease;
}

.form-group input::placeholder,
.form-group textarea::placeholder {
  color: rgba(245, 245, 245, 0.3);
}

.form-group input:focus,
.form-group textarea:focus {
  border-color: rgba(0, 188, 212, 0.45);
  background: rgba(255, 255, 255, 0.045);
}

.form-group textarea {
  min-height: 120px;
  resize: vertical;
}

.submit-button {
  width: 100%;
  margin-top: 0.3rem;
  padding: 0.8rem 1rem;
  border: 1px solid rgba(0, 188, 212, 0.45);
  border-radius: 8px;
  background: rgba(0, 188, 212, 0.1);
  color: #f5f5f5;
  font-family: inherit;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  transition:
    background 0.2s ease,
    border-color 0.2s ease,
    transform 0.2s ease;
}

.submit-button:hover:not(:disabled) {
  background: rgba(0, 188, 212, 0.16);
  border-color: rgba(0, 188, 212, 0.65);
  transform: translateY(-1px);
}

.submit-button:disabled {
  opacity: 0.55;
  cursor: not-allowed;
}

.form-message {
  margin: 1rem 0 0;
  text-align: center;
  font-size: 0.78rem;
  line-height: 1.5;
}

.success {
  color: #7dd3c7;
}

.error {
  color: #f59e9e;
}

@media (max-width: 768px) {
  .contact {
    padding: 65px 0.9rem 70px;
  }

  .section-header {
    margin-bottom: 1.8rem;
  }

  .section-title {
    margin-bottom: 0.5rem;
    font-size: 1.8rem;
  }

  .section-subtitle {
    max-width: 315px;
    font-size: 0.82rem;
    line-height: 1.55;
  }

  .contact-form {
    padding: 1rem;
    border-radius: 11px;
  }

  .form-group {
    margin-bottom: 1rem;
  }

  .form-group label {
    margin-bottom: 0.4rem;
    font-size: 0.72rem;
  }

  .form-group input,
  .form-group textarea {
    padding: 0.65rem 0.75rem;
    border-radius: 7px;
    font-size: 0.76rem;
  }

  .form-group textarea {
    min-height: 95px;
  }

  .submit-button {
    padding: 0.68rem 0.8rem;
    border-radius: 7px;
    font-size: 0.75rem;
  }

  .form-message {
    font-size: 0.7rem;
  }
}

@media (max-width: 360px) {
  .contact {
    padding: 55px 0.8rem 60px;
  }

  .section-title {
    font-size: 1.7rem;
  }

  .section-subtitle {
    max-width: 290px;
    font-size: 0.78rem;
  }

  .contact-form {
    padding: 0.9rem;
  }

  .form-group input,
  .form-group textarea {
    font-size: 0.72rem;
  }

  .form-group textarea {
    min-height: 90px;
  }
}
</style>