<template>
  <div class="subscribe-container">
    <h2 class="title">SUBSCRIBE TO OUR NEWSLETTER</h2>
    
    <div class="input-wrapper" :class="{ 'show-input': showInput }">
      <v-text-field
        v-model="email"
        placeholder="YOUR E-MAIL HERE"
        prepend-icon="mdi-email"
        variant="outlined"
        density="compact"
        class="email-input"
        persistent-placeholder
        :rules="[rules.required, rules.email]"
      ></v-text-field>
      <v-btn 
        color="primary"
        icon
        @click="handleSubmit"
        class="submit-btn"
        :disabled="!isValidEmail"
      >
        <v-icon>mdi-send</v-icon>
      </v-btn>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'

const email = ref('')
const showInput = ref(false)

const rules = {
  required: (v: string) => !!v || 'กรุณากรอกอีเมล',
  email: (v: string) => /.+@.+\..+/.test(v) || 'กรุณากรอกอีเมลให้ถูกต้อง'
}

const isValidEmail = computed(() => {
  return !!email.value && /.+@.+\..+/.test(email.value)
})

const handleSubmit = () => {
  if (isValidEmail.value) {
    console.log('Subscribing email:', email.value)
  }
}

onMounted(() => {
  setTimeout(() => {
    showInput.value = true
  }, 500)
})
</script>

<style scoped>
.subscribe-container {
  padding: 2rem;
  text-align: center;
  background-image: url('/bg.jpg');
  background-size: cover;
  background-position: center;
  filter: grayscale(100%);
}

.title {
  font-size: 1.5rem;
  color: white;
  margin-bottom: 2rem;
  font-family: 'Trajan Pro', serif;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.input-wrapper {
  display: flex;
  max-width: 500px;
  margin: 0 auto;
  align-items: center;
  gap: 8px;
  padding: 10px;
  border-radius: 30px;
  transform: translateX(-100%);
  opacity: 0;
  transition: all 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.input-wrapper.show-input {
  transform: translateX(0);
  opacity: 1;
}

.email-input {
  flex: 1;
}

.email-input :deep(.v-field) {
  border-radius: 25px;
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(5px);
  transition: all 0.3s ease;
}

.email-input :deep(.v-field:hover) {
  background: rgba(255, 255, 255, 0.2);
}

.email-input :deep(.v-field__input) {
  color: white;
  font-size: 1rem;
  letter-spacing: 0.5px;
}

.email-input :deep(.v-field__outline) {
  opacity: 0.3;
  border-color: rgba(255, 255, 255, 0.5);
}

.submit-btn {
  margin-left: 8px;
  transition: transform 0.2s ease;
}

.submit-btn:hover {
  transform: scale(1.1);
}
</style>
