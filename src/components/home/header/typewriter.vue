<template>
  <span class="text-white text-2xl md:text-4xl font-semibold mt-4 block">
    {{ displayText }}
    <span class="animate-pulse">|</span>
  </span>
</template>

<script setup>
import { ref, onMounted } from "vue";

// 👉 Props
const props = defineProps({
  texts: {
    type: Array,
    required: true,
  },
  typingSpeed: {
    type: Number,
    default: 100,
  },
  deletingSpeed: {
    type: Number,
    default: 50,
  },
  pauseTime: {
    type: Number,
    default: 1500,
  },
});

const displayText = ref("");

let wordIndex = 0;
let charIndex = 0;
let deleting = false;

function typeEffect() {
  const currentWord = props.texts[wordIndex];

  if (!deleting) {
    displayText.value = currentWord.slice(0, charIndex++);
    if (charIndex > currentWord.length) {
      deleting = true;
      setTimeout(typeEffect, props.pauseTime);
      return;
    }
  } else {
    displayText.value = currentWord.slice(0, charIndex--);
    if (charIndex === 0) {
      deleting = false;
      wordIndex = (wordIndex + 1) % props.texts.length;
    }
  }

  setTimeout(
    typeEffect,
    deleting ? props.deletingSpeed : props.typingSpeed
  );
}

onMounted(typeEffect);
</script>