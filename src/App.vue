<template>
  <div class="page">

    <!-- صورة أعلى الصفحة -->
    <div class="hero">
      <img src="./components/pics/img1.jpg" alt="header" class="hero-img" />
    </div>

    <!-- التابات تحت الصورة -->
    <header class="tabs">
      <button 
        :class="{ active: currentTab === 'contact' }"
        @click="currentTab = 'contact'"
      >
        تواصل
      </button>

      <button 
        :class="{ active: currentTab === 'work' }"
        @click="currentTab = 'work'"
      >
        أعمالي
      </button>
    </header>

    <!-- المحتوى -->
    <main>
      <Work v-if="currentTab === 'work'" />
      <Contact v-if="currentTab === 'contact'" />
    </main>

  </div>
</template>

<script setup>
import { ref } from 'vue'
import Work from './components/Work.vue'
import Contact from './components/Contact.vue'

const currentTab = ref('work')
</script>

<style scoped>
.page {
  background: white; /* خلفية الصفحة كاملة */
  min-height: 100vh;
}

/* صورة أعلى الصفحة */
.hero {
  width: 100%;
  height: auto; /* تقدر تغير الارتفاع */
  overflow: hidden;
}

.hero-img {
  width: 100%;
  height: 100%;
  object-fit: cover; /* يخلي الصورة تغطي المساحة بشكل جميل */
}

/* التابات */
.tabs {
  display: flex;
  justify-content: center;
  gap: 1rem;
  padding: 1rem;
  background: white; /* نفس لون الخلفية */
  border-bottom: 1px solid #eee; /* خط خفيف */
  margin-top: -10px; /* يقرّب التابات من الصورة */
}

button {
  padding: 0.6rem 1.2rem;
  border: none;
  background: #ddd;
  cursor: pointer;
  border-radius: 6px;
  font-size: 1rem;
}

button.active {
  background: #42b883;
  color: white;
}
</style>
