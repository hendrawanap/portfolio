<script setup>
import { onMounted, onUpdated, ref } from 'vue';

const props = defineProps(['currentSectionId']);
const navList = ref(null);
const headerRef = ref(null);
const isNavOpen = ref(false);
const currentSection = ref(null);

const toggleNav = () => {
  isNavOpen.value = !isNavOpen.value;
  if (isNavOpen.value) {
    document.body.classList.add('overflow-hidden');
  } else {
    document.body.classList.remove('overflow-hidden');
  }
};

const setCurrentSection = (section) => {
  currentSection.value = section;
};

const hideNavbar = () => {
  setTimeout(() => headerRef.value.classList.add('-translate-y-full'), 100);
};

onUpdated(() => {
  if (currentSection.value !== props.currentSectionId) {
    setCurrentSection(props.currentSectionId);
  }
});

onMounted(() => {
  window.onwheel = (e) => {
    if (!isNavOpen.value) {
      if (e.wheelDeltaY < 0) {
        headerRef.value.classList.add('-translate-y-full');
      } else {
        headerRef.value.classList.remove('-translate-y-full');
      }
    }
  };
});
</script>

<template>
  <header
    class="flex justify-between py-4 px-6 fixed top-0 left-0 right-0 z-50
    bg-black transition-transform"
    ref="headerRef"
  >
    <a href="#headline"><img class="w-8 h-8" src="../assets/logo.svg" alt="logo"></a>
    <nav>
      <ul
        class="fixed top-0 bottom-0 right-0 bg-[#1E1E1E] z-50 w-1/2 justify-center
          flex flex-col text-white text-opacity-80 transition-all text-center"
        :class="[isNavOpen ? '' : 'translate-x-full']"
        :ref="navList"
        @click="toggleNav"
      >
        <li
          class="px-4"
          :class="[currentSection === 'about-me' ? 'bg-white bg-opacity-5' : '']"
          @click="() => {
            hideNavbar();
            setCurrentSection('about-me');
          }"
        >
          <a class="text-lg my-2 block w-full" href="#about-me">About</a>
        </li>
        <li
          class="px-4"
          :class="[currentSection === 'featured-projects' ? 'bg-white bg-opacity-5' : '']"
          @click="() => {
            hideNavbar();
            setCurrentSection('featured-projects');
          }"
        >
          <a class="text-lg my-2 block w-full" href="#featured-projects">Project</a>
        </li>
        <li
          class="px-4"
          :class="[currentSection === 'contact-me' ? 'bg-white bg-opacity-5' : '']"
          @click="() => {
            hideNavbar();
            setCurrentSection('contact-me');
          }"
        >
          <a class="text-lg my-2 block w-full" href="#contact-me">Contact</a>
        </li>
        <li class="px-4">
          <a class="text-lg my-2 block w-full" href="#">My Resume</a>
        </li>
      </ul>
    </nav>
    <button @click="toggleNav">
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-menu text-primary"><line x1="3" y1="12" x2="21" y2="12"></line><line x1="3" y1="6" x2="21" y2="6"></line><line x1="3" y1="18" x2="21" y2="18"></line></svg>
    </button>
    <Teleport to="body">
      <div
        id="main-overlay"
        class="fixed inset-0 bg-black bg-opacity-80 z-40"
        :class="[isNavOpen ? 'block' : 'hidden']"
        @click="toggleNav"
      />
    </Teleport>
  </header>
</template>
