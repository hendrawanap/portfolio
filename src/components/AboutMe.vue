<script setup>
const techs = ['Javascript', 'PHP', 'Vue', 'Laravel', 'Boostrap CSS', 'Tailwind CSS', 'Node JS', 'Hapi', 'Docker', 'Firebase'];
</script>

<template>
  <section
    class="flex flex-col sm:flex-row sm:justify-between items-center"
  >
    <div class="sm:flex-1 sm:mr-12 sm:max-w-lg" data-aos="fade-right">
      <div class="flex items-center mb-8 w-full">
        <svg class="mr-3 mt-1" height="2" width="32">
          <line class="stroke-primary stroke-2" x1="0" y1="0" x2="32" y2="0" />
        </svg>
        <h4 class="text-opacity-80">About Me.</h4>
      </div>
      <p class="text-opacity-50 mb-2 md:ml-10">
        Hi, my name is Hendra. I enjoy build things using code and coffee.
        I have interest in computer science and tech stuffs especially in software engineering.
        I started to build website since my second semester in college.
      </p>
      <p class="text-opacity-50 mb-2 md:ml-10">
        Currently, I’m finishing my informatics engineering studies at Universitas Brawijaya.
        Also, I’m participating in Bangkit Academy 2022 - Cloud Computing Learning Path
        program in my 6th semester.
      </p>
      <p class="text-opacity-50 mb-2 md:ml-10">
        Here are few technologies I’ve been working with recently:
      </p>
      <ul
        class="flex flex-wrap bg-white bg-opacity-5 p-2 rounded-md
          list-disc list-inside mb-2 md:ml-10"
      >
        <li
          v-for="tech in techs"
          :key="'tech-' + tech"
          class="text-opacity-50 text-sm w-1/2 lg:w-1/3"
        >
          {{ tech }}
        </li>
      </ul>
      <p class="text-opacity-50 md:ml-10">
        In the future, I want to specialize in the backend development for some times,
        then would do DevOps stuffs.
      </p>
    </div>
    <div class="relative h-52 w-52 mt-16 cursor-pointer lg:w-72 lg:h-72" data-aos="fade-left">
      <div
        class="bg-white w-52 h-52 rounded-lg absolute -top-3 -left-3 z-20
          hover:top-0 hover:left-0 transition-all lg:w-72 lg:h-72"
      >
        <div class="relative w-52 h-52 lg:w-72 lg:h-72">
          <div class="absolute inset-0 bg-primary bg-opacity-50
            hover:bg-opacity-0 z-30 rounded-lg transition-all"/>
            <img
              class="absolute inset-0 w-52 h-52 object-cover lg:w-72 lg:h-72
                object-center rounded-lg saturate-0 hover:saturate-100"
              src="/assets/profile.png"
              alt="profile"
            >
        </div>
      </div>
      <svg class="w-52 h-52 lg:w-72 lg:h-72 absolute top-0 left-0 z-10">
        <rect class="w-52 h-52 lg:w-72 lg:h-72 fill-secondary" rx="8" ry="8"/>
      </svg>
    </div>
  </section>
</template>
