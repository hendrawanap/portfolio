<script setup>
import { onMounted, onUpdated, ref } from 'vue';

const props = defineProps(['currentSectionId']);
const headerRef = ref(null);
const isNavOpen = ref(false);
const currentSection = ref(null);
const navList = [
  { sectionIds: ['about-me'], title: 'About' },
  { sectionIds: ['featured-projects', 'other-projects'], title: 'Projects' },
  { sectionIds: ['contact-me'], title: 'Contact' },
];
const currentScrollPosition = ref(null);
const triggeredFromNav = ref(false);

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

const showNavbar = () => {
  headerRef.value.classList.remove('-translate-y-full');
};

const hideNavbar = () => {
  headerRef.value.classList.add('-translate-y-full');
};

onUpdated(() => {
  if (currentSection.value !== props.currentSectionId) {
    setCurrentSection(props.currentSectionId);
  }
});

onMounted(() => {
  window.onscroll = () => {
    if (!triggeredFromNav.value) {
      if (document.documentElement.scrollTop > currentScrollPosition.value) {
        hideNavbar();
      } else {
        showNavbar();
      }
    } else {
      triggeredFromNav.value = false;
    }
    currentScrollPosition.value = document.documentElement.scrollTop;
  };
});
</script>

<template>
  <header
    class="flex justify-between px-6 items-center fixed top-0 left-0 right-0 z-50
    bg-black transition-all"
    :class="[currentScrollPosition > 0 ? 'h-20' : 'h-24']"
    ref="headerRef"
  >
    <a href="#headline"><img class="w-10 h-10" src="../assets/logo.svg" alt="logo"></a>
    <nav>
      <ul
        class="fixed top-0 bottom-0 right-0 bg-[#1E1E1E] z-50 min-w-max w-1/2 justify-center
          flex flex-col transition-all text-center
          sm:flex-row sm:static sm:bg-transparent sm:w-auto sm:items-center"
        :class="[isNavOpen ? '' : 'translate-x-full sm:translate-x-0']"
      >
        <li
          v-for="nav, index in navList"
          :key="'nav'+index"
          class="py-4 text-opacity-80 sm:py-2 sm:px-6 sm:rounded-sm"
          :class="[nav.sectionIds.includes(currentSection) ? 'bg-white bg-opacity-5' : '']"
          @click="() => {
            triggeredFromNav = true;
            toggleNav();
            setCurrentSection(nav.sectionIds[0]);
          }"
        >
          <a
            class="text-lg block w-full sm:w-auto"
            :href="`#${nav.sectionIds[0]}`"
          >
            {{ nav.title }}
          </a>
        </li>
        <li class="px-4 sm:px-0 sm:pl-4">
          <a
            class="text-lg text-primary my-10 block w-full
              border border-primary px-4 py-2 rounded-sm
              sm:min-w-max sm:my-0"
            href="#"
          >
            My Resume
          </a>
        </li>
      </ul>
    </nav>
    <button @click="toggleNav" class="sm:hidden">
      <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-menu text-primary"><line x1="3" y1="12" x2="21" y2="12"></line><line x1="3" y1="6" x2="21" y2="6"></line><line x1="3" y1="18" x2="21" y2="18"></line></svg>
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
