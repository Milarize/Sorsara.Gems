<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { onMounted, ref } from 'vue'

const showAnimation = ref(false)

onMounted(() => {
  setTimeout(() => {
    showAnimation.value = true
  }, 1500) 
})
</script>

<template>
  <header>
    <div class="header-content">
      <img src="/logo.jpg" alt="Sorsara.Gems Logo" class="logo" :class="{ 'show-animation': showAnimation }" style="border-radius: 50%; object-fit: cover; box-shadow: 0 4px 15px rgba(0,0,0,0.1);">
      <div class="header-animation">
        <h1 class="animate-text" :class="{ 'show-animation': showAnimation }">
           Sorsara.Gems 
        </h1>
        <p class="subtitle" :class="{ 'show-animation': showAnimation }">
          เครื่องประดับอัญมณีจันทบุรี
        </p>
      </div>
    </div>
   
      <!-- <p class="subtitle" :class="{ 'show-animation': showAnimation }">
          เกี่ยวกับเรา
        </p> -->
        
   
  </header>

  <main>
    <img src="/defult.jpg" alt="Default Image" class="main-image">
  </main>

  <RouterView />
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;600;700&family=Prompt:wght@300;400;500&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@400;500;600&display=swap');

header {
  line-height: 1.5;
  max-height: 100vh;
  background: linear-gradient(135deg, #ffffff 0%, #f5f5f5 100%);
  padding: 2rem 0;
  font-family: 'Prompt', sans-serif;
}

.main-image {
  width: 100%;
  height: auto;
  object-fit: cover;
  margin-top: 2rem;
}

.header-content {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 2rem;
  padding: 0 2rem;
}

.logo {
  width: 180px;
  height: auto;
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  opacity: 0;
  transform: translateX(-30px) scale(0.95);
}

.logo.show-animation {
  animation: fadeInLeft 1.5s ease-in-out forwards;
}

.logo:hover {
  transform: scale(1.1) rotate(5deg);
}

nav {
  width: 100%;
  font-size: 1.2rem;
  text-align: center;
  margin-top: 2rem;
  font-family: 'Prompt', sans-serif;
  font-weight: 300;
  opacity: 0;
  transform: translateY(20px);
}

nav.show-animation {
  animation: fadeInUp 1.5s ease-in-out 0.8s forwards;
}

nav a.router-link-exact-active {
  color: var(--color-text);
  font-weight: bold;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0.5rem 1.5rem;
  border-left: 2px solid var(--color-border);
  transition: all 0.3s ease;
  color: #666;
}

nav a:hover {
  transform: translateY(-2px);
}

nav a:first-of-type {
  border: 0;
}

.header-animation {
  text-align: left;
}

.animate-text {
  font-family: 'Cinzel', serif;
  font-weight: 600;
  font-size: 3.2rem;
  opacity: 0;
  background: linear-gradient(45deg, #020202, #020202);
  background-size: 200% auto;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  transition: all 0.5s ease;
  animation: gradient 3s ease infinite;
  letter-spacing: 0.5px;
}

.subtitle {
  font-family: 'Prompt', sans-serif;
  font-weight: 300;
  font-size: 1.5rem;
  color: #666;
  margin-top: 1rem;
  opacity: 0;
  transform: translateY(20px);
}

.subtitle.show-animation {
  animation: fadeInUp 1.5s ease-in-out 0.5s forwards;
}

.animate-text:hover {
  transform: scale(1.05);
  letter-spacing: 1px;
}

.animate-text.show-animation {
  animation: fadeInDown 1.5s ease-in-out forwards;
}

@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-30px) scale(0.95);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

@keyframes fadeInLeft {
  from {
    opacity: 0;
    transform: translateX(-30px) scale(0.95);
  }
  to {
    opacity: 1;
    transform: translateX(0) scale(1);
  }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes gradient {
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

.brand-name {
  font-family: 'Cinzel', serif;
  letter-spacing: 0.2em;
  text-transform: uppercase;
}
</style>
