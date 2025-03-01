<script setup lang="ts">

</script>

<template>
  <div class="footer-container">
    <div class="connect-container">
      <a href="https://github.com/Choconaut">
        <img src="/github-mark-white.png" alt="GitHub Follow" />
      </a>
      <a href="https://www.linkedin.com/in/peter-n-chen/">
        <img src="/InBug-White.png" alt="LinkedIn Connect" />
      </a>
    </div>
  </div>
</template>

<style scoped>
.footer-container {
  position: relative;
  display: flex;
  flex-direction: column;
  width: 100vw;
  height: 45vh;
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  animation: gradient 15s ease infinite;
  padding-top: 5rem;
}

.footer-container::after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 50%;
  background: var(--color-background);
  clip-path: polygon(0 50%, 100% 0, 0 0);
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

@keyframes ease-in-out {
  0% {
    transform: translateY(-2rem);
  }
  100% {
    transform: translateY(-2.5rem);
  }
}

.connect-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.connect-container a img {
  width: 2rem;
  height: 2rem;
  margin: 0 1rem;
}
</style>
