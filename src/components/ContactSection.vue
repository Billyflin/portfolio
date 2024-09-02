<template>
  <section id="contact" class="mb-20">
    <h2 class="text-4xl font-bold mb-8 text-center text-gradient">Contáctame</h2>
    <div class="flex flex-wrap justify-center gap-6">
      <a v-for="link in socialLinks" :key="link.name" :href="link.url" target="_blank" rel="noopener noreferrer"
         :class="['flex items-center text-white px-6 py-3 rounded-full transition-colors', link.bgClass]">
        <component :is="link.icon" class="w-6 h-6 mr-2"/>
        <span>{{ link.name }}</span>
      </a>
    </div>
  </section>
</template>
<script>
export default {
  name: 'ContactSection',
  props: {
    socialLinks: {
      type: Array,
      required: true
    }
  }
}
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

@keyframes background-pan {
  from {
    background-position: 0% center;
  }

  to {
    background-position: -200% center;
  }
}

.text-gradient {
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

@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: .5;
  }
}

</style>