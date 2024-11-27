<template>
  <div v-if="isVisible" :class="{ 'fade-out': animationComplete }" class="animation-container">
    <lottie-player
        src="https://cdn.prod.website-files.com/613f0d51a868284d7fae6814/614b853b59e0d690c6d2788a_black.json"
        speed="1"
        :loop="false"
        :autoplay="true"
        class="fullscreen-animation"
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
      }, 2000); // Espera que la transición termine
    },
  },
};
</script>

<style scoped>
/* Contenedor de la animación */
.animation-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: 12;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, rgba(34, 0, 50, 0.94), rgba(173, 129, 205, 0.99), rgba(17, 0, 58, 0.99)); /* Fondo gradiente */
  overflow: hidden; /* Evita scroll si el Lottie es demasiado grande */
  transition: opacity 2s ease-in-out; /* Transición para opacidad */
  opacity: 1;
}

.animation-container.fade-out {
  opacity: 0;
  pointer-events: none;
}

/* Lottie a pantalla completa */
.fullscreen-animation {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  min-width: 100vw;
  min-height: 100vh;
  width: 150vh; /* Ajustar para que el Lottie siga cubriendo toda la pantalla */
  height: 150vw;
}

/* Rotación en móviles */
@media (max-width: 768px) {
  .fullscreen-animation {
    transform: translate(-50%, -50%) rotate(270deg); /* Rotar 90 grados */
    width: 150vh; /* Ajustar para que el Lottie siga cubriendo toda la pantalla */
    height: 150vw;
  }
}
</style>
