<template>
  <section id="about" class="mb-20">
    <h2 class="text-4xl font-bold mb-8 text-center text-gradient">Acerca de mí</h2>
    <div
        class="bg-gray-800 bg-opacity-50 p-8 rounded-lg shadow-lg transform hover:scale-105 transition-transform duration-300">
      <p class="text-gray-300 text-lg leading-relaxed">
        Soy un apasionado desarrollador full-stack y estudiante de Ingeniería Informática.
        Me encanta resolver problemas complejos y aprender nuevas tecnologías.
        Mi objetivo es construir aplicaciones eficientes, escalables y amigables para el usuario
        que generen un impacto positivo en la sociedad.
      </p>
    </div>
  </section>
</template>
<script>
export default {
  name: 'AboutSection'
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