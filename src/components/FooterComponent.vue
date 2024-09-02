<template>
  <footer class="bg-transparent py-8">
    <div class="container mx-auto px-4 text-center text-gray-400">
      <p>&copy; {{ new Date().getFullYear() }} Billyflin. Todos los derechos reservados. Como si fuera mi primera pag
        web jajaja</p>
    </div>
  </footer>
</template>
<script>
export default {
  name: 'FooterComponent'
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

@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: .5;
  }
}

</style>