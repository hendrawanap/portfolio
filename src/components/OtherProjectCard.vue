<script setup>
const { title, description, techs, github } = defineProps([
  'title',
  'description',
  'techs',
  'github',
]);
</script>

<template>
  <div class="flex flex-col p-6 xl:p-8 rounded-lg bg-secondary">
    <h4 class="text-primary text-opacity-80 mb-4">{{ title }}</h4>

    <p class="text-opacity-80 text-justify mb-4 leading-snug flex-1">
      {{ description }}
    </p>

    <ul class="flex text-sm mb-4">
      <li
        v-for="(tech, index) in techs"
        :key="'tech-' + index"
        class="mr-2 text-opacity-50"
      >
        {{ tech }}
      </li>
    </ul>

    <a :href="github" class="inline-block w-6 h-6" target="_blank">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="feather feather-github w-5 h-5 stroke-white opacity-80"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path
          d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"
        ></path>
      </svg>
    </a>
  </div>
</template>
