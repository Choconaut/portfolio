<script setup lang="ts">
import Navbar from '@/components/Navbar.vue'
import HomeView from '@/views/HomeView.vue'
import ProjectView from '@/views/ProjectView.vue'
import FooterView from '@/views/FooterView.vue'
import AboutMeView from '@/views/AboutMeView.vue'

import { ref, onMounted } from 'vue'

// This is a simple sticky navbar that hides when scrolling down and shows when scrolling up
const navbar = ref<HTMLElement | null>(null)
let lastScrollTop = 0;

onMounted(() => {
  window.addEventListener('scroll', () => {
    const scrollTop = window.scrollY || document.documentElement.scrollTop;
    if (scrollTop > lastScrollTop) {
      if (navbar.value) navbar.value.style.top = '-6rem';
    } else {
      if (navbar.value) navbar.value.style.top = '0';
    }
    lastScrollTop = scrollTop;
  });
});
</script>

<template>
  <div class="navbar" ref="navbar">
    <Navbar id="navigation"/>
  </div>
  <div id="home" class="main-container">
    <div class="typing-container">
      <HomeView/>
    </div>
  </div>
  <div id="projects">
    <ProjectView/>
  </div>
  <div id="about">
    <AboutMeView />
  </div>
  <div id="connect">
    <FooterView />
  </div>
</template>

<style scoped>
.main-container {
  position: relative;
  display: flex;
  flex-direction: column;
  width: 100vw;
  height: 100vh;
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  animation: gradient 15s ease infinite;
  padding-top: 5rem;
}

.main-container::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 40%;
  background: var(--color-background);
  clip-path: polygon(0 100%, 0 0, 150% 100%);
}

@keyframes gradient {
  0% {
    background-position: 0 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0 50%;
  }
}

.navbar {
  position: sticky;
  top: 0;
  z-index: 99;
  height: 0;
  transition: top 0.3s;
}

.typing-container {
  width: 100%;
  display: flex;
  margin-top: 10rem;
  justify-content: center;
}
</style>
