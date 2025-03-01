<script setup lang="ts">
import { onMounted } from 'vue'

onMounted(() => {
  const menuButtons = document.querySelectorAll(".btn")
  if (!menuButtons.length) {
    console.error("No elements with class 'btn' found")
    return;
  }
  const mobile_menu = document.querySelector(".mobile-menu")

  menuButtons.forEach(button => {
    button.addEventListener("click", () => {
      if (mobile_menu) {
        mobile_menu.classList.toggle('is-open')
      }
    });
  });
});

</script>

<template v-bind="$attrs">
  <nav>
    <a href="#connect" class="name-box">Peter Chen</a>

    <div class="menu">
      <a href="#home">Home</a>
      <a href="#projects">Projects</a>
      <a href="#about">About</a>
      <a href="#connect">Let's Connect</a>
    </div>

    <button class="btn">
      <span class="material-symbols-outlined">menu</span>
    </button>

    <div class="mobile-menu">
      <a href="#home">Home</a>
      <a href="#projects">Projects</a>
      <a href="#about">About</a>
      <a href="#connect">Let's Connect</a>
      <button class="material-symbols-rounded btn">close</button>
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
  background-color: var(--color-background);
  opacity: 50%;
  padding: 1rem 1.5rem;
  box-shadow: 0 2px 4px var(--color-box-shadow);
}

.name-box {
  color: var(--color-text);
  font-size: 1.2rem;
  text-decoration: none;
  letter-spacing: 5px;
  padding: 0.5rem calc(1rem - 5px) 0.5rem 1rem;
  border: 3px solid var(--color-text);
  transition: 0.3s;
  font-weight: bold;
  user-select: none;
}

.name-box:hover {
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

.btn {
  appearance: none;
  outline: none;
  border: none;
  background: none;
  cursor: pointer;

  display: block;
  width: 2rem;
  height: 2rem;
}

.btn span {
  color: var(--color-text);
  font-size: 2rem;
}

.btn :hover {
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
  box-shadow: var(--color-box-shadow);
  color: var(--color-text);
  transition: 0.3s;
  align-items: center;
  display: flex;
  flex-direction: column;
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
  width: 100%;
}

.mobile-menu button {
  color: var(--color-text);
  margin-top: auto;
  margin-bottom: 2rem;
}

.mobile-menu a:hover {
  color: #189ab4;
  background-color: var(--color-text);
}

@media (max-width: 768px) {
  .mobile-menu .btn {
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

  .btn {
    display: none;
  }

  .menu {
    display: flex;
  }
}
</style>
