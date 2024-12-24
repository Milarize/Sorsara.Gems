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
          <img :src="item.image" :alt="item.name" class="jewelry-image">
      
        </div>
        <div v-for="(item, index) in items" :key="'duplicate-'+index" class="jewelry-item">
          <img :src="item.image" :alt="item.name" class="jewelry-image">
        
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.jewelry-container {
  width: 100%;
  overflow: hidden;
  padding: 1rem 0;
}

.scroll-container {
  width: 100%;
  overflow: hidden;
}

.scroll-content {
  display: flex;
  animation: scroll 20s linear infinite;
  white-space: nowrap;
  gap: 1rem;
}

.jewelry-item {
  padding: 0 1rem;
  font-family: 'Prompt', sans-serif;
  transition: transform 0.3s ease;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.jewelry-image {
  width: 150px;
  height: 150px;
  object-fit: cover;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

.item-name {
  margin-top: 0.5rem;
  font-size: 1.2rem;
}

.jewelry-item:hover {
  transform: scale(1.2);
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
