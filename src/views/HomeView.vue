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

const showHeader = ref(false)
const showList = ref(false) 
const showSubscribe = ref(false)
const showAbout = ref(false)
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

  // แสดงคอมโพเนนต์ทีละอัน
  setTimeout(() => {
    showHeader.value = true
  }, 0)

  setTimeout(() => {
    showList.value = true
  }, 1000)

  setTimeout(() => {
    showSubscribe.value = true
  }, 2000)

  setTimeout(() => {
    showAbout.value = true
  }, 3000)
})

onUnmounted(() => {
  window.removeEventListener('mousemove', updateCursorPosition)
  window.removeEventListener('mouseout', hideCursor)
})
</script>

<template>
  <div style="background-color: white; min-height: 100vh; width: 100vw;">
    <Transition name="fade">
      <HeaderView v-if="showHeader" />
    </Transition>
    <Transition name="fade">
      <ListJewelry v-if="showList" />
    </Transition>
    <Transition name="fade">
      <Aboutme v-if="showAbout" />
    </Transition>
    <Transition name="fade">  
      <Subscribe v-if="showSubscribe" />
    </Transition>

    <div 
      class="cursor-follower"
      v-show="isVisible"
      :style="{
        left: cursorX + 'px',
        top: cursorY + 'px'
      }"
    ></div>
  </div>
</template>

<style scoped>
.cursor-follower {
  pointer-events: none;
  position: fixed;
  width: 20px;
  height: 20px;
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

@keyframes pulse {
  0% {
    transform: translate(-50%, -50%) scale(1);
    opacity: 0.5;
  }
  50% {
    transform: translate(-50%, -50%) scale(1.5);
    opacity: 0.2;
  }
  100% {
    transform: translate(-50%, -50%) scale(1);
    opacity: 0.5;
  }
}
</style>
