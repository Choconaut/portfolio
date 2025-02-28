<script setup lang="ts">
import { ref, onMounted } from 'vue'
import {onUnmounted} from 'vue'

const words = ["Hello World",
              "I am Peter Chen",
              "One step back, Two forward...",
              "Thanks for visiting!"]
const text = ref("")
let i = 0
let timer: ReturnType<typeof setTimeout> | null = null

function typeNow() {
  let letters = words[i].split("")
  const loopTyping = () => {
    if (letters.length > 0) {
      text.value += letters.shift()
      timer = setTimeout(loopTyping, 200)
    } else {
      // Wait for 2 seconds for readability
      timer = setTimeout(deleteNow, 2000)
    }
  }
  loopTyping()
}

function deleteNow() {
  let letters = words[i].split("")
  const loopDeleting = () => {
    if (letters.length > 0) {
      letters.pop()
      text.value = letters.join("")
      timer = setTimeout(loopDeleting, 100)
    } else {
      // Move to the next word (or loop back to the first)
      i = (i + 1) % words.length
      typeNow()
    }
  }
  loopDeleting()
}

onMounted(() => {
  typeNow()
})

onUnmounted(() => {
  if (timer) {
    clearTimeout(timer)
  }
})
</script>

<template>
  <div>
    <p>{{ text }}</p>
    <p>|</p>
  </div>
</template>

<style scoped>
div {
  display: flex;
}
p {
  font-size: 2em;
  user-select: none;
  animation:
    gradient 8s infinite;
}
p:last-of-type {
  animation:
    blink 1s infinite;
}
@keyframes blink {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
}

@keyframes gradient {
  10% {
    color: #05445e;
  }
  25% {
    color: #189ab4;
  }
  50% {
    color: #75e6da;
  }
  75% {
    color: #d4f1f4;
  }
  100% {
    color: #6d9ba9;
  }
}
</style>
