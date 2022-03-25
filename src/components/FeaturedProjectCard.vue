<script setup>import { computed, onMounted, ref } from 'vue';

const {
  title, description, techs, github, img, altSide,
} = defineProps(['title', 'description', 'techs', 'github', 'img', 'alt-side']);

const cardRef = ref(null);
const imgCardRef = ref(null);
const largeScreen = ref(false);
const BREAKPOINT = 768;

const showBgImg = () => {
  cardRef.value.style.backgroundImage = `url(${img})`;
};

const removeBgImg = () => {
  cardRef.value.style.backgroundImage = 'none';
};

const onResizeHandler = () => {
  if (window.innerWidth >= BREAKPOINT && !largeScreen.value) {
    largeScreen.value = true;
    removeBgImg();
  } else if (window.innerWidth < BREAKPOINT && largeScreen.value) {
    largeScreen.value = false;
    showBgImg();
  }
};

onMounted(() => {
  if (window.innerWidth >= BREAKPOINT) {
    largeScreen.value = true;
    removeBgImg();
  } else {
    showBgImg();
  }

  window.addEventListener('resize', onResizeHandler);
});
</script>

<template>
  <div
    class="md:grid md:grid-cols-12"
    :class="[altSide ? 'alt-side' : '']"
    data-aos="fade">
    <div
      class="hidden p-6 rounded-lg transition-all
        md:flex md:flex-col md:h-96 md:z-10
        lg:h-[28rem]"
      :class="largeScreen ? ['project-image'] : ['']"
      ref="imgCardRef"
      :style="{ backgroundImage: `url(${img})` }"
    >
    </div>
    <div
      class="flex flex-col p-6 rounded-lg sm:p-10
        md:p-6 md:z-20 md:shadow-md md:shadow-slate-900"
      :class="largeScreen ? ['project-card'] : ['project-image']"
      ref="cardRef"
      :data-aos="altSide ? 'fade-right' : 'fade-left'"
    >
      <h4 class="text-primary text-opacity-80 mb-4">{{ title }}</h4>
      <p class="text-opacity-80 mb-4 leading-snug">
        {{ description }}
      </p>
      <ul class="flex text-sm mb-4">
        <li v-for="tech, index in techs" :key="'tech-'+index" class="mr-2 text-opacity-50">
          {{ tech }}
        </li>
      </ul>
      <a :href="github" class="inline-block w-6 h-6" target="_blank">
        <svg xmlns="http://www.w3.org/2000/svg" class="feather feather-github w-5 h-5 stroke-white opacity-80" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path></svg>
      </a>
    </div>
  </div>
</template>

<style scoped>
  .project-image {
    background-size: cover;
    background-position: center top;
    background-color: black;
    background-blend-mode: luminosity;
    box-shadow: inset 0 0 0 2000px rgba(20, 39, 78, 0.95);
  }

  @media screen and (min-width: 768px) {
    .alt-side .project-card {
      grid-column-start: 1;
      grid-column-end: -5;
      grid-row-start: -2;
      grid-row-end: 1;
      @apply bg-secondary;
    }

    .alt-side .project-image {
      grid-column-start: -10;
      grid-column-end: -1;
      grid-row-start: -3;
      grid-row-end: 2;
    }

    .project-card {
      grid-column-start: 5;
      grid-column-end: -1;
      grid-row-start: -2;
      grid-row-end: 1;
      @apply bg-secondary;
    }

    .project-image {
      grid-column-start: 1;
      grid-column-end: 10;
      grid-row-start: -3;
      grid-row-end: 2;
    }

    .project-image:hover {
      box-shadow: inset 0 0 0 2000px rgba(20, 39, 78, 0.15);
      background-color: transparent;
    }
  }

  @media screen and (min-width: 1024px) {
    .alt-side .project-card {
      grid-column-start: -6;
      grid-column-end: 1;
    }

    .alt-side .project-image {
      grid-column-start: -1;
      grid-column-end: -9;
    }

    .project-card {
      grid-column-start: 6;
      grid-column-end: -1;
    }

    .project-image {
      grid-column-start: 1;
      grid-column-end: 9;
    }
  }
</style>
