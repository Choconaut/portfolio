<script setup lang="ts">
import { ref, onMounted } from 'vue'
import {onUnmounted} from 'vue'

const words = ["Hello World",
              "I am Peter Chen, a fullstack developer",
              "I used my thinking muscles for this one",
              "Thanks for visiting!",
              "One step back, two forward",
              "Every journey has its final day, don't rush",
              ]
const text = ref("")
let i = 0
let timer: ReturnType<typeof setTimeout> | null = null

function typeNow() {
  const letters = words[i].split("")
  const loopTyping = () => {
    if (letters.length > 0) {
      text.value += letters.shift()
      timer = setTimeout(loopTyping, 175)
    } else {
      // Wait for 2 seconds for readability
      timer = setTimeout(deleteNow, 2000)
    }
  }
  loopTyping()
}

function deleteNow() {
  const letters = words[i].split("")
  const loopDeleting = () => {
    if (letters.length > 0) {
      letters.pop()
      text.value = letters.join("")
      timer = setTimeout(loopDeleting, 100)
    } else {
      // Move to the next word (or loop back to the first)
      i = (i + 1) % words.length
      timer = setTimeout(typeNow, 1000)
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
  animation: gradient 8s ease infinite;

  @media (max-width: 768px) {
    font-size: 1.3em;
  }
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
  0%   { color: #ffffff; text-shadow: 1px 1px 3px rgba(0,0,0,0.15); }
  25%  { color: #e1f5fe; text-shadow: 1px 1px 3px rgba(0,0,0,0.15); }
  50%  { color: #b3e5fc; text-shadow: 1px 1px 3px rgba(0,0,0,0.15); }
  75%  { color: #81d4fa; text-shadow: 1px 1px 3px rgba(0,0,0,0.15); }
  100% { color: #ffffff; text-shadow: 1px 1px 3px rgba(0,0,0,0.15); }
}

</style>
