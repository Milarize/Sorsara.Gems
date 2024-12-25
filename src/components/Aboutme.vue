<template>
  <div class="about-container" v-show="!isLoading">
    <div class="gems-header">
      <img src="/Gem.jpg" alt="Ruby Gemstones" class="header-gems">
      <h1 class="animate-text">About Sor Sara Gems</h1>
    </div>

    <div class="content">
      <div class="text-content">
        <p class="subtitle">Welcome to Sor Sara Gems, where we specialize in premium quality gemstones.</p>
        <p class="subtitle">With years of expertise in the gemstone industry, we carefully select and curate 
           the finest stones for our collection.</p>
      </div>
      
      <div class="gems-gallery">
        <img src="/Gem2.jpg" alt="Mixed Gemstones" class="gallery-gems">
      </div>
    </div>
  </div>

  <div v-if="isLoading" class="loading-screen"></div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isLoading = ref(true)

onMounted(() => {
  setTimeout(() => {
    isLoading.value = false
  }, 1400)
})
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;600;700&family=Prompt:wght@300;400;500&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@400;500;600&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.loading-screen {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background: white;
  z-index: 9999;
}

.about-container {
  width: 100%;
  max-width: 1200px;
  margin: 4rem auto;
  padding: 2rem;
  font-family: 'Prompt', sans-serif;
}

@media (min-width: 768px) {
  .about-container {
    padding: 2rem;
  }
}

.gems-header {
  position: relative;
  text-align: center;
  margin-bottom: 2rem;
}

@media (min-width: 768px) {
  .gems-header {
    margin-bottom: 3rem;
  }
}

.header-gems {
  width: 100%;
  max-height: 300px;
  object-fit: cover;
  border-radius: 8px;
  margin-bottom: 0.8rem;
  opacity: 0;
  animation: fadeInDown 1.2s ease-in-out forwards;
}

@media (min-width: 768px) {
  .header-gems {
    max-height: 400px;
    border-radius: 12px;
    margin-bottom: 1rem;
  }
}

.animate-text {
  font-family: 'Cinzel', serif;
  font-weight: 500;
  font-size: clamp(1.2rem, 5vw, 2.5rem);
  opacity: 0;
  background: linear-gradient(45deg, #dc9090, #020202, #dc9090);
  background-size: 200% auto;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  transition: all 0.5s ease;
  animation: fadeInDown 1.2s ease-in-out forwards, textGradient 3s ease infinite;
  letter-spacing: 0.3px;
  margin: 0.8rem 0;
}

.content {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2rem;
  align-items: center;
  margin-top: 3rem;
}

@media (min-width: 768px) {
  .content {
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
  }
}

.text-content {
  font-size: 1rem;
  line-height: 1.5;
  color: #444;
}

@media (min-width: 768px) {
  .text-content {
    font-size: 1.1rem;
    line-height: 1.6;
  }
}

.subtitle {
  font-family: 'Prompt', sans-serif;
  font-weight: 300;
  font-size: clamp(0.9rem, 3vw, 1.2rem);
  color: #666;
  margin-top: 0.5rem;
  opacity: 0;
  transform: translateY(15px);
  animation: fadeInUp 1.2s ease-in-out 0.4s forwards;
}

.gallery-gems {
  width: 100%;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;
  opacity: 0;
  animation: fadeInLeft 1.2s ease-in-out 0.6s forwards;
}

@media (min-width: 768px) {
  .gallery-gems {
    border-radius: 12px;
  }
}

.gallery-gems:hover {
  transform: scale(1.02);
}

@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-20px) scale(0.95);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

@keyframes fadeInLeft {
  from {
    opacity: 0;
    transform: translateX(-20px) scale(0.95);
  }
  to {
    opacity: 1;
    transform: translateX(0) scale(1);
  }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(15px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes textGradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

</style>
