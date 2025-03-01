<script setup lang="ts">
document.addEventListener('DOMContentLoaded', () => {
  const projects = document.querySelectorAll('.project');

  // Threshold for when a project should be considered in view
  const observerOptions = {
    threshold: 0.7,
  };

  const observer = new IntersectionObserver((entries, observer) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('in-view');
        observer.unobserve(entry.target);
      }
    });
  }, observerOptions);

  projects.forEach(project => {
    observer.observe(project);
  });
});
</script>

<template>
<div class="project-container">
  <div class="divider">
    <div class="project">
      <a href="https://dev.parcelsearch.com" class="project-image">
        <div class="image-container">
          <img src="/parcel-search.png" alt="parcel-search image">
        </div>
      </a>
      <div class="project-description">
        <h3>Parcel Search</h3>
        <p>Full Stack Data Viewer Webapp built with Vue.js,
        PostgreSQL, Springboot, and AWS Lightsail</p>
      </div>
    </div>

    <div class="project">
      <div class="project-description">
        <h3>Tank Game</h3>
        <p>Game  developed in JavaFX to demonstrate OOP design principles </p>
      </div>
      <a href="https://github/choconaut/tankgame.com" class="project-image">
        <div class="image-container">
          <img src="/tankgame.png" alt="tank-game image">
        </div>
      </a>
    </div>
  </div>
</div>
</template>

<style scoped>
.project-container {
  width: 100vw;
  background: var(--color-background);
  padding-top: 5rem;
  color: var(--color-text);

  @media (max-width: 675px) {
    padding-top: 1rem;
  }
}

.divider {
  display: grid;
  margin-left: 1rem;
  margin-right: 1rem;
  gap: 5rem;
}

.project {
  display: flex;
  flex-direction: row;
  opacity: 0;
  transition: transform 0.6s ease-out, opacity 0.6s ease-out;
}

.project:nth-child(odd) {
  transform: translateX(-50px);
}

/* For even projects: slide in from right */
.project:nth-child(even) {
  transform: translateX(50px);
  justify-content: flex-end;
}

/* When in view, reset transform and opacity */
.project.in-view {
  opacity: 1;
  transform: translateX(0);
}

.project-image {
  height: 25rem;
  width: 45rem;
  background: skyblue;
  display: flex;
  align-items: center;
  transition: 0.3s;

  @media (max-width: 675px) {
    height: 13rem;
    width: 20rem;
  }

  @media (min-width: 676px) and (max-width: 749px) {
    height: 15rem;
    width: 35rem;
  }

  @media (min-width: 750px) and (max-width: 850px) {
    height: 20rem;
    width: 40rem;

  }

  @media (min-width: 1400px) {
    height: 35rem;
    width: 60rem;
  }
}

.project-image:nth-child(even) {
  justify-content: flex-end;
}

.project-image:hover {
  transform: translateY(-2rem);
  transition: all 0.3s ease-in-out;
  box-shadow: 10px 1rem 1rem lightskyblue;
}

.project-description {
  z-index: 97;
  height: 100%;
  width: 30%;
  margin-top: 2.5rem;

  @media (max-width: 675px) {
    background-color: rgba(128, 128, 128, 0.3);
    height: 85%;
    margin-top: 1rem;
  }

  @media (min-width: 676px) and (max-width: 850px) {
    background-color: rgba(128, 128, 128, 0.3);
    height: 85%;
    margin-top: 1.3rem;

  }
}

.project-description:nth-child(even) {
  transform: translateX(-0.5rem);

  @media (max-width: 675px) {
    transform: translateX(-1.5rem);
  }

  @media (min-width: 1000px) {
    transform: translateX(-1rem);
  }
}

.project-description:nth-child(odd) {
  transform: translateX(3rem);

  @media (max-width: 675px) {
    transform: translateX(1.5rem);
  }

  @media (min-width: 1000px) {
    transform: translateX(3rem);
  }
}

.project-description h3 {
  font-size: 2rem;
  font-weight: bold;

  @media (max-width: 675px) {
    font-size: 0.8rem;
  }

  @media (min-width: 676px) and (max-width: 768px) {
    font-size: 1.5rem;
  }

  @media (min-width: 1000px) {
    font-size: 2.5rem;
  }
}

.project-description p {
  margin-top: 1.5rem;
  font-size: 1rem;

  @media (max-width: 675px) {
    font-size: 0.6rem;
  }

  @media (min-width: 676px) and (max-width: 768px) {
    font-size: 0.8rem;
  }

  @media (min-width: 1000px) {
    font-size: 1.2rem;
  }
}

.image-container {
  display: flex;
  opacity: 75%;
  width: 90%;
  height: 75%;
  margin: 1px;
}

.image-container img {
  width: 100%;
  height: 100%;
  image-rendering: smooth;
  object-fit: fill;
}

</style>
