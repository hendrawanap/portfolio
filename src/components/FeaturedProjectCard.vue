<script setup>
const {
  title, description, techs, github, img,
} = defineProps(['title', 'description', 'techs', 'github', 'img']);
</script>

<template>
  <div class="relative">
    <div class="flex flex-col p-6 rounded-lg card" :style="{'background-image': `url(${img})`}">
      <h4 class="text-primary text-opacity-80 mb-4">{{ title }}</h4>
      <p class="text-opacity-80 mb-4 text-sm leading-tight">
        {{ description }}
      </p>
      <ul class="flex text-xs mb-4">
        <li v-for="tech, index in techs" :key="'tech-'+index" class="mr-2 text-opacity-50">
          {{ tech }}
        </li>
      </ul>
      <a :href="github" class="inline-block w-4 h-4">
        <svg xmlns="http://www.w3.org/2000/svg" class="feather feather-github w-4 h-4 stroke-white opacity-80" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path></svg>
      </a>
    </div>
  </div>
</template>

<style scoped>
  .card {
    background-size: cover;
    background-position: center top;
    background-color: black;
    background-blend-mode: luminosity;
    box-shadow: inset 0 0 0 2000px rgba(8, 25, 60, 0.95);
  }
</style>
