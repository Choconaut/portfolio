<script setup lang="ts">
import { onMounted } from 'vue'

onMounted(() => {
  const hamburger = document.querySelector(".hamburger")
  if (!hamburger) {
    console.error("Element with class 'hamburger' not found")
    return;
  }
  const hamburger_icon = hamburger.querySelector("span")
  const mobile_menu = document.querySelector(".mobile-menu")

  hamburger.addEventListener("click", () => {
    if (hamburger_icon) {
      hamburger_icon.innerText = hamburger_icon.innerText === 'menu'
        ? 'close'
        : 'menu';
    }
    if (mobile_menu) {
      mobile_menu.classList.toggle('is-open')
    }
  })
})
</script>

<template>
  <nav>
    <h1>Peter Chen</h1>

    <div class="menu">
      <a href="#home">Home</a>
      <a href="#projects">Projects</a>
      <a href="#about">About Me</a>
      <a href="#connect">Let's Connect</a>
    </div>

    <button class="hamburger">
      <span class="material-symbols-outlined">menu</span>
    </button>

    <div class="mobile-menu">
      <router-link class="link" to="/">Home</router-link>
      <router-link class="link" to="/projects">Projects</router-link>
      <router-link class="link" to="/about">About</router-link>
      <router-link class="link" to="/contact">Contact</router-link>
    </div>
  </nav>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: var(--color-background)
}

nav {
  position: relative;
  z-index: 98;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: var(--color-text);
  padding: 1rem 1.5rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

nav h1 {
  letter-spacing: 5px;
  padding: 0.5rem calc(1rem - 5px) 0.5rem 1rem;
  border: 3px solid var(--color-text);
  transition: 0.3s;
  font-weight: bold;
}

nav h1:hover {
  color: #189ab4;
}

.menu {
  display: none;
  align-items: center;
  margin: 0 -1rem;
}

.menu a {
  margin: 0 1rem;
  color: var(--color-text);
  text-decoration: none;
  transition: 0.3s;
  font-size: 1.25rem;
  font-weight: bold;
}

.menu a:hover {
  color: #189ab4;
}

.hamburger {
  appearance: none;
  outline: none;
  border: none;
  background: none;
  cursor: pointer;

  display: block;
  width: 2rem;
  height: 2rem;
}

.hamburger span {
  color: var(--color-text);
  font-size: 2rem;
}

.hamburger :hover {
  color: #189ab4;
}

.mobile-menu {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 99;

  padding-top: 6rem;
  opacity: 0;
  transform: translateY(-100%);
  background-color: var(--color-background);
  color: var(--color-text);
  transition: 0.3s;
}

.mobile-menu.is-open {
  opacity: 1;
  transform: translateY(0);
}

.mobile-menu a {
  display: block;
  padding: 1rem;
  color: var(--color-text);
  text-align: center;
  text-decoration: none;
  font-size: 1.25rem;
  transition: 0.3s;
}

.mobile-menu a:hover {
  color: #189ab4;
  background-color: var(--color-text);
}

@media (max-width: 768px) {
  .mobile-menu .hamburger {
    display: flex;
  }

  .menu {
    display: none;
  }
}

@media (min-width: 769px) {
  .mobile-menu {
    display: none;
  }

  .hamburger {
    display: none;
  }

  .menu {
    display: flex;
  }
}
</style>
