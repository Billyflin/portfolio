<template>
  <div class="relative min-h-screen overflow-hidden bg-gray-900 text-gray-100">
    <!-- Blob Background -->
    <div ref="blob" class="blob"></div>
    <div class="blur"></div>
    <LottieAnimation is-visible></LottieAnimation>

    <!-- Main Content -->
    <div class="relative z-10">
      <!-- Header -->
      <HeaderComponent/>

      <!-- Hero Section -->
      <Hero/>

      <!-- Main Content -->
      <main class="container mx-auto px-4 py-16">
        <!-- About Section -->
        <AboutSection/>

        <!-- Skills Section -->
        <SkillSection/>


        <!-- Certifications Section-->
        <CertificationsSection/>
      </main>

      <!-- Footer -->
      <FooterComponent/>
    </div>
  </div>
</template>

<script setup>
import {ref, onMounted, onUnmounted} from 'vue';
import Hero from "./components/Hero.vue";
import SkillSection from "./components/SkillSection.vue";
import AboutSection from "./components/AboutSection.vue";
import FooterComponent from "./components/FooterComponent.vue";
import HeaderComponent from "./components/HeaderComponent.vue";
import CertificationsSection from "./components/CertificationsSection.vue";
import LottieAnimation from "./components/LottieAnimation.vue";
import LottieLoader from "./components/LottieLoader.vue";

const blob = ref(null);

const handleBlobAnimation = (event) => {
  const {clientX, clientY} = event;
  blob.value.animate({
    left: `${clientX}px`,
    top: `${clientY}px`
  }, {duration: 3000, fill: "forwards"});
};

onMounted(() => {
  if (blob.value) {
    window.addEventListener('pointermove', handleBlobAnimation);
  }
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('pointermove', handleBlobAnimation);
  window.removeEventListener('scroll', handleScroll);
});
</script>

<style scoped>
@keyframes rotate {
  from {
    rotate: 0deg;
  }
  50% {
    scale: 1 1.5;
  }
  to {
    rotate: 360deg;
  }
}

.blob {
  height: 20vmax;
  aspect-ratio: 1;
  position: fixed;
  z-index: 1;
  left: 50%;
  top: 50%;
  translate: -50% -50%;
  border-radius: 50%;
  background: linear-gradient(
      to right,
      rgb(123, 31, 162),
      rgb(103, 58, 183),
      rgb(244, 143, 177),
      rgb(123, 31, 162)
  );
  animation: rotate 20s infinite;
  opacity: 0.8;
}

.blur {
  height: 100%;
  width: 100%;
  position: fixed;
  z-index: 2;
  backdrop-filter: blur(11vmax);
}

</style>
