<script setup lang="ts">
import { RouterView } from 'vue-router'
import Navbar from '@/components/Navbar.vue'
import HomeView from '@/views/HomeView.vue'
import ProjectView from '@/views/ProjectView.vue'
import FooterView from '@/views/FooterView.vue'
import AboutMeView from '@/views/AboutMeView.vue'
</script>

<template>
  <div class="main-container">
    <Navbar />
    <div class="typing-container">
      <HomeView />
    </div>
  </div>
  <ProjectView />
  <AboutMeView />
  <FooterView />
</template>

<style scoped>
.main-container {
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  width: 100vw;
  height: 100vh;
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  animation: gradient 15s ease infinite;
}

.main-container::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 40%;
  background: white;
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

.typing-container {
  width: 100%;
  display: flex;
  margin-top: 10rem;
  justify-content: center;
}

</style>
