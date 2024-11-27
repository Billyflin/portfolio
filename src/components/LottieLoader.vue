<template>
    <div class="animation-container">
      <lottie-player
          :src="llamita"
          speed="1"
          :loop="true"
          :autoplay="true"
          class="responsive-animation"
      ></lottie-player>
    </div>
</template>

<script>
import "@lottiefiles/lottie-player";

export default {
  name: "LottieLoader",
  props: {
    isVisible: {
      type: Boolean,
      default: true,
    },
  },
  data() {
    return {
      llamita:null
    };
  },
  methods: {
    async loadAnimation() {
      const filellamita = await import("/src/assets/llamita.json")
      this.llamita = JSON.stringify(filellamita.default);

    },
  },
  mounted() {
    this.loadAnimation();
  },
};
</script>

<style scoped>
.animation-container {
  width: 100%;
  height: 100%;
  position: fixed;
  z-index: 12;
}

.responsive-animation {
  width: 100%;
  height: auto;
}
</style>
