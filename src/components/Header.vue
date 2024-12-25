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
      <img src="/logo.jpg" alt="Sorsara.Gems Logo" class="logo" :class="{ 'show-animation': showAnimation }"
        style="border-radius: 50%; object-fit: cover; box-shadow: 0 4px 15px rgba(0,0,0,0.1);">
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


  <RouterView />
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;600;700&family=Prompt:wght@300;400;500&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@400;500;600&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

header {
  line-height: 1.2;
  max-height: 80vh;
  background: #f5f5f5;
  padding: 1rem 0;
  font-family: 'Prompt', sans-serif;
}

.main-image {
  width: 100%;
  height: auto;
  object-fit: cover;
  margin-top: 1rem;
}

.header-content {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  padding: 0 1rem;
  flex-wrap: wrap;
}

.logo {
  width: clamp(80px, 15vw, 120px);
  height: auto;
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  opacity: 0;
  transform: translateX(-20px) scale(0.95);
}

.logo.show-animation {
  animation: fadeInLeft 1.2s ease-in-out forwards;
}

.logo:hover {
  transform: scale(1.05) rotate(3deg);
}

nav {
  width: 100%;
  font-size: clamp(0.8rem, 1.5vw, 1rem);
  text-align: center;
  margin-top: 1rem;
  font-family: 'Prompt', sans-serif;
  font-weight: 300;
  opacity: 0;
  transform: translateY(15px);
}

nav.show-animation {
  animation: fadeInUp 1.2s ease-in-out 0.6s forwards;
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
  padding: 0.3rem 1rem;
  border-left: 1px solid var(--color-border);
  transition: all 0.3s ease;
  color: #666;
}

nav a:hover {
  transform: translateY(-1px);
}

nav a:first-of-type {
  border: 0;
}

.header-animation {
  text-align: left;
}

.animate-text {
  font-family: 'Cinzel', serif;
  font-weight: 500;
  font-size: clamp(1.5rem, 4vw, 2.5rem);
  opacity: 0;
  background: linear-gradient(45deg, #dc9090, #020202, #dc9090);
  background-size: 200% auto;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  transition: all 0.5s ease;
  animation: textGradient 3s ease infinite;
  letter-spacing: 0.3px;
}

.subtitle {
  font-family: 'Prompt', sans-serif;
  font-weight: 300;
  font-size: clamp(0.8rem, 2vw, 1.2rem);
  color: #666;
  margin-top: 0.5rem;
  opacity: 0;
  transform: translateY(15px);
}

.subtitle.show-animation {
  animation: fadeInUp 1.2s ease-in-out 0.4s forwards;
}

.animate-text:hover {
  transform: scale(1.03);
  letter-spacing: 0.5px;
}

.animate-text.show-animation {
  animation: fadeInDown 1.2s ease-in-out forwards, textGradient 3s ease infinite;
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

.brand-name {
  font-family: 'Cinzel', serif;
  letter-spacing: 0.15em;
  text-transform: uppercase;
}

@media (max-width: 768px) {
  .header-content {
    flex-direction: column;
    text-align: center;
    gap: 0.8rem;
  }

  .header-animation {
    text-align: center;
  }

  nav a {
    padding: 0.3rem 0.8rem;
  }
}

@media (max-width: 480px) {
  header {
    padding: 0.8rem 0;
  }

  .header-content {
    padding: 0 0.8rem;
  }

  nav a {
    padding: 0.3rem 0.5rem;
    font-size: 0.8rem;
  }
}
</style>
