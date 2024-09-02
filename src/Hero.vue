<template>
  <section class="relative min-h-screen flex items-center justify-center overflow-hidden py-20 font-roboto">
    <div class="text-center z-10 px-4 max-w-3xl mx-auto">
      <h1 class="text-2xl text-violet-100 sm:text-3xl md:text-4xl lg:text-5xl font-bold mb-6 flex flex-col items-center justify-center text-center leading-tight">
        <span class="mb-2">Hola, soy Billy Martínez, aunque</span>
        <span class="mb-2"> en con un computador soy</span>
        <magic-text-span
            texto-resaltar="Billyflin"
            additional-classes=" transition duration-300 text-4xl
            sm:text-5xl md:text-6xl lg:text-7xl my-4"
        />
        <span class="mt-2">Como Bruce Wayne y Batman,</span>
        <span>pero con más código y menos murciélagos.</span>
        <span class="text-sm sm:text-base md:text-lg mt-4 text-gray-900 font-bold">Igual de oscuro</span>
      </h1>

      <div class="flex items-center justify-center space-x-4 mt-8 mb-10">
        <TerminalIcon class="w-6 h-6 md:w-8 md:h-8 text-gradient animate-pulse"/>
        <changing-text
            :texts="[
            'Estudiante de Ingeniería Informática',
            'Desarrollador Mobile Entusiasta',
            'Creador Frontend Apasionado',
            'Amante de la Tecnología y la Innovación',
            'Fanático de los Videojuegos y el Anime',
            'Adicto a el Café',
            'Te acordaste de el juego :P'
          ]"
            :interval="4000"
            :typingSpeed="40"
            class="text-base sm:text-lg md:text-xl animate-fade-in-up animation-delay-600 text-gray-300 leading-relaxed"
        />
      </div>

      <div class="flex flex-col sm:flex-row items-center justify-center space-y-4 sm:space-y-0 sm:space-x-4">
        <a href="#skills"
           class="inline-block bg-gradient-to-r from-blue-500 to-purple-600 text-white px-6 py-3 rounded-full font-bold hover:from-blue-600 hover:to-purple-700 transition-all duration-300 animate-fade-in-up animation-delay-900 transform hover:scale-105 text-sm sm:text-base">
          Explorar mis habilidades
        </a>
        <a href="#projects"
           class="inline-block bg-gradient-to-r from-pink-500 to-red-600 text-white px-6 py-3 rounded-full font-bold hover:from-pink-600 hover:to-red-700 transition-all duration-300 animate-fade-in-up animation-delay-1000 transform hover:scale-105 text-sm sm:text-base">
          Ver mis proyectos
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import {TerminalIcon} from 'lucide-vue-next';
import MagicTextSpan from "./components/MagicTextSpan.vue";
import ChangingText from "./components/ChangingText.vue";
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap');

@keyframes rotate {
  from {
    rotate: 0deg;
  }
  50% {
    scale: 1 1.7;
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

.animate-fade-in-up {
  animation: fadeInUp 0.6s ease-out forwards;
}

.animation-delay-600 {
  animation-delay: 600ms;
}

.animation-delay-900 {
  animation-delay: 900ms;
}

.animation-delay-1000 {
  animation-delay: 1000ms;
}

.font-roboto {
  font-family: "Roboto", sans-serif;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.text-gradient {
  animation: background-pan 3s linear infinite;
  background: linear-gradient(
      to right,
      #3b82f6,
      #8b5cf6,
      #ec4899,
      #3b82f6
  );
  background-size: 200%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
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