<script setup lang="ts">
import { ref, onMounted } from 'vue'

const jewelryList = [
  { image: '/jewelryList/diamond.jpg', name: 'เพชร' },
  { image: '/jewelryList/ring.jpg', name: 'แหวน' },
  { image: '/jewelryList/necklace.jpg', name: 'สร้อย' },
  { image: '/jewelryList/crown.jpg', name: 'มงกุฎ' },
  { image: '/jewelryList/ruby.jpg', name: 'ทับทิม' },
  { image: '/jewelryList/bracelet.jpg', name: 'กำไล' }
]

const items = ref(jewelryList)
</script>

<template>
  <div class="jewelry-container">
    <div class="scroll-container">
      <div class="scroll-content">
        <div v-for="(item, index) in items" :key="index" class="jewelry-item">
          <div class="image-container">
            <img :src="item.image" :alt="item.name" class="jewelry-image">
          </div>
        </div>
        <div v-for="(item, index) in items" :key="'duplicate-'+index" class="jewelry-item">
          <div class="image-container">
            <img :src="item.image" :alt="item.name" class="jewelry-image">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.jewelry-container {
  width: 100%;
  overflow: hidden;
  padding: 0.5rem 0;
}

.scroll-container {
  width: 100%;
  overflow: hidden;
}

.scroll-content {
  display: flex;
  animation: scroll 20s linear infinite;
  white-space: nowrap;
  gap: 0.5rem;
}

.jewelry-item {
  padding: 0 0.2rem;
  font-family: 'Prompt', sans-serif;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.image-container {
  width: 250px;
  height: 250px;
  overflow: hidden;

  box-shadow: 0 6px 12px rgba(0,0,0,0.2);
 
}

.jewelry-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.jewelry-item:hover .jewelry-image {
  transform: scale(1.2);
}

.item-name {
  margin-top: 0.5rem;
  font-size: 1.2rem;
}

@keyframes scroll {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}
</style>
