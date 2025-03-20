<script setup lang="ts">
document.addEventListener("DOMContentLoaded", () => {
  const cards = document.querySelectorAll(".description, .card-frame");
  const observer = new IntersectionObserver((entries, obs) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const index = Array.from(cards).indexOf(entry.target);
        setTimeout(() => {
          entry.target.classList.add("in-view");
          obs.unobserve(entry.target);
        }, index * 200); // 300ms between each card
      }
    });
  }, { threshold: 0.4 });

  cards.forEach(card => observer.observe(card));
});
</script>

<template>
<div class="about-me-container">
  <div class="card-frame">
    <div class="description">
    I’m a software engineer who loves tackling challenging problems and exploring
    new technologies. Whether it’s designing clean, maintainable backends or
    experimenting with dynamic frontends, I enjoy turning ideas into reality.
    When I’m not coding, I’m likely playing strategy or RPGs that inspire logical
    thinking and creativity.
    </div>
  </div>
</div>
</template>

<style scoped>
.about-me-container {
  height: 120vh;
  display: flex;
  background: var(--color-background);
  justify-content: center;
  align-items: center;

  @media(max-width: 560px) {
    height: 80vh;
  }
}

/* outer darker card */
.card-frame {
  position: relative;
  height: 40rem;
  width: 60rem;
  transform: rotate(7deg);
  background-color: #0D1B2A;
  overflow: visible;
  opacity: 0;

  @media(max-width: 560px) {
    height: 30vh;
    width: 85vw;
  }

  @media(min-width: 560px) and (max-width: 1200px) {
    height: 50vh;
    width: 70vw;
  }
}

.card-frame.in-view {
  animation: slide-in 0.5s ease-in-out forwards;
  opacity: 1;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
}

.description {
  height: 40rem;
  width: 60rem;
  padding: 2rem 3rem;
  opacity: 0;
  color: #FFFFFF;
  font-size: clamp(0.6rem, 1.5vw, 1.5rem);
  display: flex;
  align-items: center;
  background: linear-gradient(135deg, #0077DD 40%, #005BB5 100%);
  border: 5px solid #0D1B2A;
  font-family: 'Roboto Condensed', sans-serif;
  text-transform: uppercase;
  transition: transform .2s ease, box-shadow .2s ease;
  letter-spacing: 0.05em;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
  position: relative;
  overflow: hidden;

  @media(max-width: 560px) {
    height: 30vh;
    width: 85vw;
  }

  @media(min-width: 560px) and (max-width: 1200px) {
    height: 50vh;
    width: 70vw;
  }
}

.description::before {
  content: "";
  position: absolute;
  top: -10%;
  right: -25%;
  width: 150%;
  height: 30%;
  background: rgba(255,255,255,0.15);
  transform: rotate(25deg);
  pointer-events: none;
}

.description::after {
  content: "ABOUT ME";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  padding: 0.5rem 1rem;
  background: rgba(13,27,42,0.85);
  font-size: 1.25rem;
  text-align: center;
}

.description::after {
  content: "";
  position: absolute;
  inset: 5px; /* Slightly inset */
  pointer-events: none;
  z-index: -1;
}


.description:hover {
  transform: rotate(20deg) scale(1.05);
  box-shadow: 0 15px 40px rgba(0,0,0,0.5);
}

.description.in-view {
  animation: slide-in 0.5s ease-in-out forwards;
  opacity: 1;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
}

@keyframes slide-in {
  0% {
    transform: rotate(10deg) translateX(-100%);
  }
  100% {
    transform: rotate(10deg) translateX(0);
  }
}
</style>
