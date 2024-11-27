<template>
  <section class="relative min-h-screen flex items-center justify-center overflow-hidden py-20 font-roboto">
    <div class="text-center z-10 px-4 max-w-3xl mx-auto">
      <!-- Título principal -->
      <h1 class="text-2xl sm:text-3xl md:text-4xl lg:text-5xl font-bold mb-6 flex flex-col items-center justify-center text-center leading-tight text-white">
        <span class="mb-2">Hola, soy Billy Martínez, aunque</span>
        <span class="mb-2">con un computador soy</span>
        <magic-text-span
            texto-resaltar="Billyflin"
            additional-classes=" transition duration-300 text-4xl sm:text-5xl md:text-6xl lg:text-7xl my-4 text-violet-500"
        />
        <span class="mt-2 text-xl text-gray-300">Como Bruce Wayne y Batman,</span>
        <span class="mt-2 text-xl text-gray-300">pero con más código y menos murciélagos.</span>
      </h1>

      <!-- Cambios dinámicos de texto -->
      <div class="flex items-center justify-center space-x-4 mt-8 mb-10">
        <TerminalIcon class="w-6 h-6 md:w-8 md:h-8 text-gradient animate-pulse" />
        <changing-text
            :texts="[ 'Estudiante de Ingeniería Informática', 'Desarrollador Mobile Entusiasta', 'Creador Frontend Apasionado', 'Amante de la Tecnología y la Innovación', 'Fanático de los Videojuegos y el Anime', 'Adicto al Café', 'Te acordaste del juego :P' ]"
            :interval="4000"
            :typingSpeed="40"
            class="text-base sm:text-lg md:text-xl text-gray-300 leading-relaxed"
        />
      </div>

      <!-- Botones -->
      <div class="flex flex-col sm:flex-row items-center justify-center space-y-4 sm:space-y-0 sm:space-x-4">
<!--        <a-->
<!--            href="#skills"-->
<!--            class="inline-block bg-gradient-to-r from-blue-500 to-purple-600 text-white px-6 py-3 rounded-full font-bold hover:from-blue-600 hover:to-purple-700 transition-all duration-300 transform hover:scale-105 text-sm sm:text-base shadow-lg"-->
<!--        >-->
<!--          Explorar mis habilidades-->
<!--        </a>-->
<!--        <a-->
<!--            href="#projects"-->
<!--            class="inline-block bg-gradient-to-r from-pink-500 to-red-600 text-white px-6 py-3 rounded-full font-bold hover:from-pink-600 hover:to-red-700 transition-all duration-300 transform hover:scale-105 text-sm sm:text-base shadow-lg"-->
<!--        >-->
<!--          Ver mis proyectos-->
<!--        </a>-->
        <a
            href="/Billy_Martinez_CV.pdf"
            target="_blank"
            download
            class="inline-block flex items-center bg-gradient-to-r from-green-500 to-blue-600 text-white px-6 py-3 rounded-full font-bold hover:from-green-600 hover:to-blue-700 transition-all duration-300 transform hover:scale-125 text-xl-center sm:text-base shadow-lg space-x-2"
        >
          <FileDownIcon class="w-5 h-5" />
          <span>Descargar mi CV</span>
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { TerminalIcon, FileDownIcon } from 'lucide-vue-next';
import MagicTextSpan from "./MagicTextSpan.vue";
import ChangingText from "./ChangingText.vue";
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap');

.font-roboto {
  font-family: "Roboto", sans-serif;
}

/* Gradiente animado en texto */
.text-gradient {
  animation: background-pan 3s linear infinite;
  background: linear-gradient(to right, #3b82f6, #8b5cf6, #ec4899, #3b82f6);
  background-size: 200%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

/* Animaciones */
@keyframes background-pan {
  from {
    background-position: 0% center;
  }
  to {
    background-position: -200% center;
  }
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}
</style>
