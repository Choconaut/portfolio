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
  <div id="about" class="about-me-container">
    <div class="header">
      <h2>About Me</h2>
      <hr/>
    </div>
    <AboutMeView />
  </div>
  <div id="projects" class="project-container">
    <div class="header">
      <h2>Projects</h2>
      <hr/>
    </div>
    <ProjectView/>
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
  height: 115vh;
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  animation: gradient 15s ease infinite;
  padding-top: 5rem;

  @media(max-width: 768px) {
    padding-top: 2rem;
    height: 90vh;
  }
}

.main-container::after {
  content: "";
  position: absolute;
  bottom: -1%;
  left: 0;
  width: 100%;
  height: 41%;
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

.header {
  display: flex;
  flex-direction: column;
  text-align: center;
  align-items: center;
  margin-bottom: 2rem;
  padding: 2rem 0;
  width: 100%;

  @media(max-width: 768px) {
    padding: 1rem 0;
    margin-bottom: 1rem;
  }

  h2 {
    background: linear-gradient(45deg, #23a6d5, #e73c7e);
    -webkit-background-clip: text;
    color: transparent;
    font-size: clamp(1.5rem, 2.5vw, 3rem);
  }

  hr {
    border: none;
    height: 4px;
    width: 80%;
    background: linear-gradient(90deg, #23a6d5, #e73c7e);
  }
}

.typing-container {
  position: absolute;
  width: 100%;
  display: flex;
  margin-top: 10rem;
  justify-content: center;
  top: 20%;
  transform: translateY(-50%);
}

.about-me-container {
  display: flex;
  align-items: center;
  flex-direction: column;
}

.project-container {
  padding-bottom: 2rem;
}
</style>
