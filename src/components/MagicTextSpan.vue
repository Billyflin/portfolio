<template>
 <span :class="['relative inline-block', additionalClasses]">
    <span v-for="star in stars" :key="star" class="magic-star">
      <svg viewBox="0 0 512 512">
            <defs>
      <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" style="stop-color:rgb(123,31,162);stop-opacity:1"/>
        <stop offset="100%" style="stop-color:rgb(244,143,177);stop-opacity:1"/>
      </linearGradient>
    </defs>
        <path
            fill="url(#grad1)"
            d="M512 255.1c0 11.34-7.406 20.86-18.44 23.64l-171.3 42.78l-42.78 171.1C276.7 504.6 267.2 512 255.9 512s-20.84-7.406-23.62-18.44l-42.66-171.2L18.47 279.6C7.406 276.8 0 267.3 0 255.1c0-11.34 7.406-20.83 18.44-23.61l171.2-42.78l42.78-171.1C235.2 7.406 244.7 0 256 0s20.84 7.406 23.62 18.44l42.78 171.2l171.2 42.78C504.6 235.2 512 244.6 512 255.1z"
        />
      </svg>
    </span>
    <span class="magic-text">{{ textoResaltar }}</span>
 </span>
</template>

<script setup>
import {defineProps, onMounted, ref} from 'vue';

const props = defineProps({
  textoResaltar: {
    type: String,
    required: true,
  },
  additionalClasses: {
    type: String,
    default: '',
  },
});

const stars = ref([1, 2, 3]);

const rand = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;

const animate = (star) => {
  if (props.textoResaltar.length < 0) {
    return;
  }
  star.style.setProperty("--star-left", `${rand(-10, 100)}%`);
  star.style.setProperty("--star-top", `${rand(-40, 80)}%`);

  star.style.animation = "none";
  star.offsetHeight;
  star.style.animation = "";
};

onMounted(() => {
  const starElements = document.querySelectorAll('.magic-star');

  starElements.forEach((star, index) => {
    setTimeout(() => {
      animate(star);
      setInterval(() => animate(star), 1000);
    }, index * 333);
  });
});
</script>

<style scoped>
@keyframes background-pan {
  from {
    background-position: 0% center;
  }
  to {
    background-position: -200% center;
  }
}

@keyframes scale {
  from, to {
    transform: scale(0);
  }
  50% {
    transform: scale(1);
  }
}

@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(180deg);
  }
}

.title {
  color: white;
  font-family: "Rubik", sans-serif;
  font-size: clamp(2em, 2vw, 4em);
  font-weight: 400;
  margin: 0px;
  padding: 20px;
  text-align: center;
}

.magic {
  display: inline-block;
  position: relative;
}

.magic-star {
  --size: clamp(20px, 1.5vw, 30px);

  animation: scale 700ms ease forwards;
  display: block;
  height: var(--size);
  left: var(--star-left);
  position: absolute;
  top: var(--star-top);
  width: var(--size);
}

.magic-star > svg {
  animation: rotate 1000ms linear infinite;
  display: block;
  opacity: 0.7;
}

.magic-text {
  animation: background-pan 3s linear infinite;
  background: linear-gradient(
      to right,
      rgb(123, 31, 162),
      rgb(103, 58, 183),
      rgb(244, 143, 177),
      rgb(123, 31, 162)
  );
  background-size: 200%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  white-space: nowrap;
}
</style>
