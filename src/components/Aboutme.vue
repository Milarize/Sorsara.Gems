<template>
  <div class="about-container">
    <div class="gems-header">
      <img src="/Gem.jpg" alt="Ruby Gemstones" class="header-gems">
      <h1>About Sor Sara Gems</h1>
    </div>

    <div class="content">
      <div class="text-content">
        <p>Welcome to Sor Sara Gems, where we specialize in premium quality gemstones.</p>
        <p>With years of expertise in the gemstone industry, we carefully select and curate 
           the finest stones for our collection.</p>
      </div>
      
      <div class="gems-gallery">
        <img src="/Gem2.jpg" alt="Mixed Gemstones" class="gallery-gems">
      </div>
    </div>
  </div>
</template>

<style scoped>
.about-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

.gems-header {
  position: relative;
  text-align: center;
  margin-bottom: 3rem;
}

.header-gems {
  width: 100%;
  max-height: 400px;
  object-fit: cover;
  border-radius: 12px;
  margin-bottom: 1rem;
}

h1 {
  color: #333;
  font-size: 2.5rem;
  margin: 1rem 0;
}

.content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
  align-items: center;
}

.text-content {
  font-size: 1.1rem;
  line-height: 1.6;
  color: #444;
}

.gallery-gems {
  width: 100%;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;
}

.gallery-gems:hover {
  transform: scale(1.02);
}

@media (max-width: 768px) {
  .content {
    grid-template-columns: 1fr;
  }
  
  .gems-header h1 {
    font-size: 2rem;
  }
}
</style>
