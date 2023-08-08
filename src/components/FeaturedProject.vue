<script setup>
import FeaturedProjectCard from './FeaturedProjectCard.vue';

const BASE_IMG_PATH = '/assets/images';

const featuredProjects = [
  {
    title: "Hospital's Outpatient System",
    description:
      "A web-based hospital's outpatient system which mainly consists of outpatient's registration & queues functionalities. Applied 'Clean Architecture' concepts in design & implementation process.",
    techs: [
      'SvelteKit',
      'Tailwind CSS',
      'Express.js',
      'TypeScript',
      'MongoDB',
      'Pusher',
    ],
    github: '#',
    img: `${BASE_IMG_PATH}/outpatient-system.png`,
  },
  {
    title: 'Didow App: Dyslexia Therapy at Home',
    description:
      "An android mobile application to help kids with dyslexia to learn how to read and write in a fun way. I was contributed in developing & deploying the back-end web services to support the app's functionalities.",
    techs: ['Android', 'Hapi.js', 'FastAPI', 'Firebase', 'Google Cloud Run'],
    github: 'https://github.com/hendrawanap/didow-api',
    img: `${BASE_IMG_PATH}/didow.png`,
  },
  {
    title: 'IF ELSE 2021',
    description:
      'A web application to facilitate informatics engineering freshmen student of FILKOM UB in their journey at 2021 student orientation program.',
    techs: ['Laravel', 'Vue', 'Bootstrap CSS'],
    github: 'https://github.com/hendrawanap/ifelse2021',
    img: `${BASE_IMG_PATH}/ifelse2021.png`,
  },
  {
    title: 'Caloreal',
    description:
      'A web application to help people in measuring their calories requirements and plan their diet accordingly.',
    techs: ['Laravel', 'Livewire', 'Bootstrap CSS'],
    github: 'https://github.com/hendrawanap/daking',
    img: `${BASE_IMG_PATH}/caloreal.png`,
  },
];
</script>

<template>
  <section>
    <div class="flex items-center mb-8 w-full">
      <svg class="mr-3 mt-1" height="2" width="32">
        <line class="stroke-primary stroke-2" x1="0" y1="0" x2="32" y2="0" />
      </svg>
      <h4 class="text-opacity-80">Things I've Built.</h4>
    </div>
    <div class="md:pl-10">
      <FeaturedProjectCard
        v-for="(featuredProject, index) in featuredProjects"
        :key="'featured-' + index"
        :title="featuredProject.title"
        :description="featuredProject.description"
        :techs="featuredProject.techs"
        :github="featuredProject.github"
        :img="featuredProject.img"
        class="mb-6 md:mb-10 lg:mb-12"
        :alt-side="index % 2 === 1"
      />
    </div>
  </section>
</template>
