<template>
  <div class="changing-text" aria-live="polite">
    <transition name="fade" mode="out-in">
      <p :key="currentTextIndex" class="typed-text">
        {{ displayedText }}
        <span class="cursor" :class="{ 'typing': isTyping }">|</span>
      </p>
    </transition>
  </div>
</template>

<script setup>
import { ref, computed, watch, onMounted, onUnmounted } from 'vue';

const props = defineProps({
  texts: {
    type: Array,
    required: true,
    validator: (value) => value.length > 0
  },
  interval: {
    type: Number,
    default: 3000
  },
  typingSpeed: {
    type: Number,
    default: 50
  }
});

const currentTextIndex = ref(0);
const displayedText = ref('');
const isTyping = ref(true);

let intervalId;
let typingIntervalId;

const currentFullText = computed(() => props.texts[currentTextIndex.value] || '');

const typeText = () => {
  const targetText = currentFullText.value;
  let charIndex = 0;

  clearInterval(typingIntervalId);
  isTyping.value = true;

  typingIntervalId = setInterval(() => {
    if (charIndex < targetText.length) {
      displayedText.value += targetText[charIndex];
      charIndex++;
    } else {
      clearInterval(typingIntervalId);
      isTyping.value = false;
    }
  }, props.typingSpeed);
};

const changeText = () => {
  isTyping.value = true;
  displayedText.value = '';
  currentTextIndex.value = (currentTextIndex.value + 1) % props.texts.length;
  typeText();
};

watch(() => props.texts, () => {
  currentTextIndex.value = 0;
  changeText();
}, {immediate: true});

onMounted(() => {
  if (props.texts.length > 0) {
    typeText();
    intervalId = setInterval(changeText, props.interval);
  }
});

onUnmounted(() => {
  clearInterval(intervalId);
  clearInterval(typingIntervalId);
});
</script>

<style scoped>
.changing-text {
  min-height: 1.5em; /* Adjust based on your font size to prevent layout shifts */
}

.typed-text {
  display: inline-block;
}

.cursor {
  display: inline-block;
  width: 3px;
  background-color: currentColor;
  margin-left: 2px;
  animation: blink 0.7s infinite;
}

.cursor.typing {
  animation: none;
}

@keyframes blink {
  0% {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>