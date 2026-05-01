<template>
  <div class="project">

    <!-- يمين: العنوان والوصف -->
    <div class="info">
      <h3 class="title">{{ title }}</h3>
      <p class="desc">{{ description }}</p>
    </div>

    <!-- يسار: السلايدر الرأسي -->
    <div class="slider">

      <!-- زر علوي -->
      <button class="arrow up" @click="moveUp">▲</button>

      <!-- صورتين فقط -->
      <div class="images-window">
        <img 
          v-for="(img, index) in visibleImages" 
          :key="index" 
          :src="img" 
          class="slide-img"
          @click="openImage(img)"
        />
      </div>

      <!-- زر سفلي -->
      <button class="arrow down" @click="moveDown">▼</button>

    </div>

    <!-- نافذة تكبير الصورة -->
    <div v-if="preview" class="preview" @click="preview = null">
      <img :src="preview" class="preview-img" />
    </div>

  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const title = "مشروع 1"
const description = "وصف مختصر للمشروع."

// استيراد 6 صور
import img1 from './pics/img1.jpg'
import img2 from './pics/img2.jpg'
import img3 from './pics/img3.jpg'
import img4 from './pics/img4.jpg'
import img5 from './pics/img5.jpg'
import img6 from './pics/img6.jpg'

const images = [img1, img2, img3, img4, img5, img6]

// مؤشر بداية السلايدر
const index = ref(0)

// إظهار صورتين فقط
const visibleImages = computed(() => {
  return images.slice(index.value, index.value + 2)
})

// تحريك للأعلى
function moveUp() {
  if (index.value > 0) {
    index.value--
  }
}

// تحريك للأسفل
function moveDown() {
  if (index.value < images.length - 2) {
    index.value++
  }
}

// تكبير الصورة
const preview = ref(null)
function openImage(img) {
  preview.value = img
}
</script>

<style scoped>
.project {
  background: white;
  padding: 1.5rem;
  border-radius: 12px;
  display: flex;
  justify-content: space-between;
  gap: 2rem;
  margin-bottom: 2rem;
  box-shadow: 0 2px 10px rgba(0,0,0,0.08);
}

/* يمين */
.info {
  width: 35%;
}

.title {
  margin-bottom: 0.5rem;
  color: #2c3e50;
  font-size: 1.4rem;
}

.desc {
  color: #555;
}

/* يسار: السلايدر */
.slider {
  width: 40%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.7rem;
}

.arrow {
  background: #42b883;
  color: white;
  border: none;
  padding: 0.5rem 0.8rem;
  border-radius: 6px;
  cursor: pointer;
  font-size: 1.1rem;
}

.images-window {
  display: flex;
  flex-direction: column;
  gap: 0.7rem;
  width: 100%;
}

.slide-img {
  width: 100%;
  height: 150px;
  object-fit: cover;
  border-radius: 6px;
  cursor: pointer;
  transition: 0.2s;
}

.slide-img:hover {
  transform: scale(1.03);
}

/* نافذة تكبير الصورة */
.preview {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.85);
  display: flex;
  justify-content: center;
  align-items: center;
}

.preview-img {
  max-width: 90%;
  max-height: 90%;
  border-radius: 8px;
}

@media (max-width: 600px) {
  .project {
    flex-direction: column;
    text-align: center;
  }

  .info {
    width: 100%;
  }

  .slider {
    width: 100%;
  }

  .slide-img {
    height: 180px;
  }

  .arrow {
    padding: 0.4rem 0.7rem;
  }
}


</style>
