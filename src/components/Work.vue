<template>
  <section>
   

    <div class="projects">
      <Project1 />
      <Project2 />
      <Project3 />
     <!--  <Project4 />
      <Project5 /> -->
    </div>
  </section>
</template>

<script setup>
import Project1 from './Projects/project1/Project1.vue'
import Project2 from './Projects/project2/Project2.vue'
import Project3 from './Projects/project3/Project3.vue'

</script>

<style scoped>
.projects {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  margin-top: 1rem;
}
</style>
