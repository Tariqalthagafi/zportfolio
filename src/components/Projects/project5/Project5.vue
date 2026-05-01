<template>
  <div class="project">

    <h3 class="title">{{ title }}</h3>
    <p class="desc">{{ description }}</p>

    <!-- معرض الصور -->
    <div class="gallery">
      <img 
        v-for="(img, index) in images" 
        :key="index" 
        :src="img" 
        class="gallery-img"
        @click="openImage(img)"
      />
    </div>

    <!-- نافذة تكبير الصورة -->
    <div v-if="preview" class="preview" @click="preview = null">
      <img :src="preview" class="preview-img" />
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue'

/* بيانات المشروع */
const title = "مشروع 5"
const description = "وصف مختصر للمشروع الخامس."

/* استيراد الصور من مجلد pics */
import img1 from './pics/img1.jpg'
import img2 from './pics/img2.jpg'
import img3 from './pics/img3.jpg'

const images = [img1, img2, img3]

/* تكبير الصورة */
const preview = ref(null)
function openImage(img) {
  preview.value = img
}
</script>

<style scoped>
.project {
  padding: 1rem;
  background: #eef;
  border-radius: 8px;
  margin-bottom: 1.5rem;
}

.title {
  margin-bottom: 0.5rem;
  color: #2c3e50;
}

.desc {
  margin-bottom: 1rem;
  color: #555;
}

.gallery {
  display: flex;
  gap: 0.7rem;
  flex-wrap: wrap;
}

.gallery-img {
  width: 140px;
  height: 100px;
  object-fit: cover;
  border-radius: 6px;
  cursor: pointer;
  transition: 0.2s;
}

.gallery-img:hover {
  transform: scale(1.05);
}

.preview {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.8);
  display: flex;
  justify-content: center;
  align-items: center;
}

.preview-img {
  max-width: 90%;
  max-height: 90%;
  border-radius: 8px;
}
</style>
