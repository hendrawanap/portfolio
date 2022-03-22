<script setup>
import { onMounted, ref } from 'vue';
import Header from './components/CustomHeader.vue';
import Headline from './components/MyHeadline.vue';
import AboutMe from './components/AboutMe.vue';
import FeaturedProject from './components/FeaturedProject.vue';
import OtherProject from './components/OtherProject.vue';
import Contact from './components/ContactMe.vue';
import Footer from './components/CustomFooter.vue';

const headlineRef = ref(null);
const aboutMeRef = ref(null);
const featuredProjectRef = ref(null);
const otherProjectRef = ref(null);
const contactRef = ref(null);
const currentSectionId = ref(null);
const scrollHandler = (entries, observer) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      const isEnough = entry.intersectionRatio * entry.target.offsetHeight
        > 0.75 * window.innerHeight;
      if (entry.intersectionRatio >= 0.75 || isEnough) {
        currentSectionId.value = entry.target.id;
        history.replaceState(undefined, undefined, `#${entry.target.id}`);
      }
    }
  });
};
const buildThresholdList = ({ steps } = { steps: 10 }) => {
  const thresholds = [];
  const numSteps = steps;

  for (let i = 1.0; i <= numSteps; i += 1) {
    const ratio = i / numSteps;
    thresholds.push(ratio);
  }

  thresholds.push(0);
  return thresholds;
};

const observer = new IntersectionObserver(scrollHandler, {
  root: document, threshold: buildThresholdList(),
});

onMounted(() => {
  observer.observe(headlineRef.value.$el);
  observer.observe(aboutMeRef.value.$el);
  observer.observe(featuredProjectRef.value.$el);
  observer.observe(otherProjectRef.value.$el);
  observer.observe(contactRef.value.$el);
});
</script>

<template>
  <div id="root">
    <Header :current-section-id="currentSectionId"/>
    <main class="px-8 container mx-auto">
      <Headline class="pt-20" id="" ref="headlineRef"/>
      <AboutMe class="mt-16 pt-20" id="about-me" ref="aboutMeRef"/>
      <FeaturedProject class="mt-16 pt-20" id="featured-projects" ref="featuredProjectRef"/>
      <OtherProject id="other-projects" ref="otherProjectRef"/>
      <Contact class="my-16 pt-20" id="contact-me" ref="contactRef"/>
    </main>
    <Footer/>
  </div>
</template>

<style>
body {
  font-family: 'Outfit', Arial, sans-serif;
  scroll-behavior: smooth;
}

body h1,
body h2,
body h3,
body h4,
body p,
body span,
body ul li,
body li,
body label,
body input,
body textarea {
  @apply text-white
}

body .mono {
  font-family: 'Oxygen Mono', Courier, monospace;
}

body h2 {
  @apply text-4xl font-semibold;
}

body h4 {
  @apply text-xl font-semibold;
}

body p {
  @apply text-base leading-snug;
}
</style>
