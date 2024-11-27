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
      this.animationComplete = true; // Activa la transición al completar
      setTimeout(() => {
        this.$emit("close"); // Emite un evento al padre para ocultar el componente
      }, 1500); // Espera a que termine la transición antes de cerrar
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
  background: linear-gradient(135deg, rgba(15, 7, 19, 0.99), rgba(255, 255, 255, 0.99)); /* Fondo gradiente */
  transition: opacity 0.5s ease-in-out; /* Transición suave para la opacidad */
  opacity: 1;
}

.animation-container.fade-out {
  opacity: 0; /* Desaparece el fondo */
  z-index: -1;
}

.responsive-animation {
  width: 100%;
  height: auto;
}
</style>
