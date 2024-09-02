<template>
  <div id="about" class="min-h-screen flex items-center justify-center p-4">
    <div class="w-full max-w-xl md:max-w-5xl bg-gray-800 rounded-2xl shadow-2xl overflow-hidden">
      <div class="flex flex-col md:flex-row">
        <!-- Imagen ocupando más espacio en pantallas pequeñas -->
        <div class="md:w-2/5 bg-gray-700">
          <div class="relative h-64 md:h-full">
            <img
                :src="billyflin"
                alt="Billy Martínez"
                class="w-full h-full object-contain object-top transition-all duration-900 ease-in-out"
                @load="onImageLoad"
                :class="{ 'opacity-0 scale-105': !imageLoaded, 'opacity-100 scale-100': imageLoaded }"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-gray-900 via-gray-900/50 to-transparent"></div>
          </div>
        </div>
        <!-- Contenido con ocultamiento en pantallas pequeñas -->
        <div class="p-6 md:p-8 w-full md:w-3/5 flex flex-col justify-between">
          <div>
            <h2 class="text-3xl md:text-4xl font-bold mb-2 text-white">Billy Martínez</h2>
            <p class="text-lg md:text-xl text-gray-300 mb-6">Estudiante de Ingeniería Informática</p>
            <div class="space-y-3 mb-8">
              <div class="flex items-center text-gray-300">
                <MapPinIcon class="w-5 h-5 mr-3 text-gray-400" />
                <a href="https://www.ufro.cl">Universidad de la Frontera, Chile</a>
              </div>
              <div class="flex items-center text-gray-300">
                <MailIcon class="w-5 h-5 mr-3 text-gray-400" />
                <a href="mailto:billymartinezc@gmail.com">Billymartinezc@gmail.com</a>
              </div>
            </div>
            <!-- Ocultar este bloque en pantallas pequeñas -->
            <div class="space-y-4 text-gray-300 hidden md:block">
              <p class="animate-fade-in">
                Soy un estudiante de 4to año de Ingeniería Informática, apasionado por la tecnología. He adquirido experiencia en desarrollo de software e investigación en realidad virtual.
              </p>
              <p class="animate-fade-in" style="animation-delay: 200ms;">
                Mi experiencia abarca desde el desarrollo de aplicaciones para bancos digitales hasta la investigación en realidad virtual para el campo de la enfermería. Me especializo en tecnologías como Vue.js, Spring, y Kotlin, y tengo experiencia en despliegue de aplicaciones utilizando AWS y Google Cloud.
              </p>
              <p class="animate-fade-in" style="animation-delay: 400ms;">
                Actualmente, estoy explorando <magic-text-span texto-resaltar="Kotlin Multiplataforma"></magic-text-span> para el desarrollo de aplicaciones móviles. Estoy emocionado por las oportunidades que me esperan después de graduarme y siempre estoy buscando nuevos desafíos donde pueda seguir creciendo y aprendiendo.
              </p>
            </div>
          </div>
          <!-- Botones con espacio reducido para pantallas pequeñas -->
          <div class="flex flex-col md:flex-row space-y-4 md:space-y-0 md:space-x-4 mt-8">
            <button class="bg-gray-700 hover:bg-gray-600 text-white font-semibold py-3 px-6 rounded-full flex items-center justify-center space-x-2 transition duration-300 shadow-lg hover:shadow-xl">
              <GithubIcon class="w-5 h-5" />
              <span>GitHub</span>
            </button>
            <button class="bg-gradient-to-r from-indigo-800 to-fuchsia-900 hover:bg-blue-700 text-white font-semibold py-3 px-6 rounded-full flex items-center justify-center space-x-2 transition duration-300 shadow-lg hover:shadow-xl">
              <LinkedinIcon class="w-5 h-5" />
              <span>LinkedIn</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>




<script setup>
import { ref } from 'vue';
import { MapPinIcon, MailIcon, GithubIcon, LinkedinIcon } from 'lucide-vue-next';
import billyflin from '../assets/img/file.png';
import MagicTextSpan from "./MagicTextSpan.vue";

const imageLoaded = ref(false);

const onImageLoad = () => {
  imageLoaded.value = true;
};
</script>

<style scoped>
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}


.animate-fade-in {
  animation: fadeIn 0.8s ease-out forwards;
}
</style>