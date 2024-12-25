<script lang="ts" setup>
import HeaderView from '../components/Header.vue'
import ListJewelry from '../components/ListJewelry.vue'
import Subscribe from '../components/Subscribe.vue'
import Aboutme from '../components/Aboutme.vue'
import { ref, onMounted, onUnmounted } from 'vue'

const cursorX = ref(0)
const cursorY = ref(0)
const isVisible = ref(false)
const targetX = ref(0)
const targetY = ref(0)

const updateCursorPosition = (e: MouseEvent) => {
  targetX.value = e.clientX
  targetY.value = e.clientY
  isVisible.value = true
}

const hideCursor = () => {
  isVisible.value = false
}

const smoothCursor = () => {
  const easing = 0.15
  cursorX.value += (targetX.value - cursorX.value) * easing
  cursorY.value += (targetY.value - cursorY.value) * easing
  requestAnimationFrame(smoothCursor)
}

onMounted(() => {
  window.addEventListener('mousemove', updateCursorPosition)
  window.addEventListener('mouseout', hideCursor)
  smoothCursor()
})

onUnmounted(() => {
  window.removeEventListener('mousemove', updateCursorPosition)
  window.removeEventListener('mouseout', hideCursor)
})
</script>

<template>
  <div class="app-container">
    <header class="header">
      <HeaderView />
      <v-divider class="header-divider"></v-divider>
    </header>

    <main class="main-content">
      <section class="about-section">
        <Aboutme />
        <v-divider class="section-divider"></v-divider>
      </section>

      <section class="jewelry-section">
        <ListJewelry />
      </section>

      <section class="subscribe-section">
        <Subscribe />
      </section>
    </main>

    <div class="cursor-follower" v-show="isVisible" :style="{
      left: cursorX + 'px',
      top: cursorY + 'px'
    }"></div>
  </div>
</template>

<style scoped>
.app-container {
  width: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 100;
  background: rgba(255, 255, 255, 0.95);
}

.main-content {
  margin-top: 80px;
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 4rem;
  padding: 2rem 0;
}

.section-divider {
  margin: 2rem 0;
  border-color: rgba(0, 0, 0, 0.1);
  width: 100%;
}

.about-section,
.jewelry-section,
.subscribe-section {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.cursor-follower {
  pointer-events: none;
  position: fixed;
  width: clamp(10px, 2vw, 20px);
  height: clamp(10px, 2vw, 20px);
  background: rgba(255, 192, 203, 0.5);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  z-index: 9999;
  mix-blend-mode: difference;
  animation: pulse 2s infinite;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

@media (max-width: 768px) {
  .main-content {
    gap: 2rem;
    padding: 1rem;
  }

  .about-section,
  .jewelry-section,
  .subscribe-section {
    padding: 0 1rem;
  }
}
</style>
