<script setup>
import OtherProjectCard from './OtherProjectCard.vue';

const otherProjects = [
  {
    title: 'Quiz API',
    description: 'A backend/api application to serve quiz data to the quiz app android application and quiz admin web application.',
    techs: ['Node JS', 'Hapi', 'Firebase', 'GCP'],
    github: 'https://github.com/hendrawanap/quiz-api',
  },
  {
    title: 'Quiz Admin',
    description: 'A web application to manage quiz data.',
    techs: ['Vue', 'Vite', 'Tailwind CSS', 'Firebase'],
    github: 'https://github.com/hendrawanap/quiz-admin-vue3',
  },
  {
    title: 'Management Competition 2022',
    description: 'Maintaining and adding features for existing FBE UAJY event “Management Competition 2022” website.',
    techs: ['Laravel', 'Bootstrap CSS'],
    github: 'https://github.com/hendrawanap/uajy_mc',
  },
];
</script>

<template>
 <section>
    <h4 class="text-opacity-80 text-center mb-6">
      Other Projects.
    </h4>
    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-4 xl:gap-6">
      <OtherProjectCard
        v-for="otherProject, index in otherProjects"
        :key="'other-'+index"
        :title="otherProject.title"
        :description="otherProject.description"
        :techs="otherProject.techs"
        :github="otherProject.github"
        class="mb-6 sm:mb-0"
      />
    </div>
 </section>
</template>
