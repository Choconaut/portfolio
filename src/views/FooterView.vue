<script setup lang="ts">
  const resumeLink = `${import.meta.env.BASE_URL}peter_chen_resume.pdf`;
</script>

<template>
  <div class="footer-container">
    <div class="connect-container">
      <div class="links">
        <a href="https://github.com/Choconaut">
          <img src="/github-mark-white.png" alt="GitHub Follow" />
        </a>
        <a href="https://www.linkedin.com/in/peter-n-chen/">
          <img src="/InBug-White.png" alt="LinkedIn Connect" />
        </a>
      </div>
      <a
        :href="resumeLink"
        download="peter_chen_resume.pdf"
        class="resume"
      >
        Download My Resume
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
  height: 51%;
  bottom: -1%;
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
  flex-direction: column;
  height: 100%;
  gap: 1rem;
}

.connect-container a img {
  width: 2rem;
  height: 2rem;
  margin: 0 1rem;
}

.resume {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 5px;
  padding: 0.5rem 1rem;
  border: 2px solid #f9e8d0;
  border-radius: 5px;
  color: #f9e8d0;
  font-size: 1rem;
  text-decoration: none;
}

.resume:hover {
  background-color: rgba(249, 232, 208, 0.2);
  color: #fffaf6;
}
</style>
