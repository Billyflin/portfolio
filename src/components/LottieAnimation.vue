<template>
  <div v-if="isVisible" :class="{ 'fade-out': animationComplete }" class="animation-container">
    <lottie-player
        src="https://cdn.prod.website-files.com/613f0d51a868284d7fae6814/614b853b59e0d690c6d2788a_black.json"
        speed="1"
        :loop="false"
        :autoplay="true"
        class="responsive-animation"
        @complete="onAnimationComplete"
    ></lottie-player>
  </div>
</template>

<script>
import "@lottiefiles/lottie-player";

export default {
  name: "PageTransition",
  props: {
    isVisible: {
      type: Boolean,
      default: true,
    },
  },
  data() {
    return {
      animationComplete: false, // Controla si la animación ha terminado
    };
  },
  methods: {
    onAnimationComplete() {
      this.animationComplete = true; // Inicia el fade-out
      setTimeout(() => {
        this.$emit("close"); // Emite el evento para notificar al padre
      }, 2000); // Espera que la transición termine (igual a `transition` en CSS)
    },
  },
};
</script>

<style scoped>
.animation-container {
  width: 100%;
  height: 100%;
  position: fixed;
  z-index: 12;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, rgba(34, 0, 50, 0.94), rgba(173, 129, 205, 0.99), rgba(17, 0, 58, 0.99)); /* Fondo gradiente */
  transition: opacity 2s ease-in-out; /* Transición suave */
  opacity: 1;
}

.animation-container.fade-out {
  opacity: 0; /* Desaparece */
  pointer-events: none; /* Permite interactuar con elementos detrás */
}

.responsive-animation {
  width: 100%;
  height: auto;
}
</style>
