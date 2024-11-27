<template>
  <div id="about" class="min-h-screen flex items-center justify-center p-4">
    <div class="w-full max-w-xl md:max-w-7xl bg-gray-800 rounded-2xl shadow-2xl overflow-hidden">
      <div class="flex flex-col md:flex-row">
        <!-- Imagen ocupando más espacio en pantallas pequeñas -->
        <div class="md:w-2/5 bg-gray-700">
          <div class="relative h-64 md:h-full">
            <!-- Loader -->
            <div
                v-if="!imageLoaded"
                class="absolute inset-0 flex items-center justify-center bg-gray-900/50"
            >
              <div class="loader"></div>
            </div>

            <!-- Imagen -->
            <img
                :src="billyflin"
                alt="Billy Martínez"
                class="w-full h-full object-cover object-top transition-all duration-900 ease-in-out"
                @load="onImageLoad"
                :class="{ 'opacity-0 scale-105': !imageLoaded, 'opacity-100 scale-100': imageLoaded }"
            />

            <!-- Gradiente -->
            <div class="absolute inset-0 bg-gradient-to-t from-gray-900/70 via-gray-900/10 to-transparent"></div>
          </div>

        </div>
        <!-- Contenido con ocultamiento en pantallas pequeñas -->
        <div class="p-6 md:p-8 w-full md:w-3/5 flex flex-col justify-between">
          <div>
            <h2 class="text-3xl md:text-4xl font-bold mb-2 text-white">Billy Martínez</h2>
            <p class="text-lg md:text-xl text-gray-300 mb-6">Apasionado por la Innovación Tecnológica</p>
            <div class="space-y-3 mb-8">
              <div class="flex items-center text-gray-300">
                <MapPinIcon class="w-5 h-5 mr-3 text-gray-400" />
                <a href="https://www.ufro.cl" target="_blank" rel="noopener noreferrer">Universidad de la Frontera, Chile</a>
              </div>
              <div class="flex items-center text-gray-300">
                <MailIcon class="w-5 h-5 mr-3 text-gray-400" />
                <a href="mailto:billymartinezc@gmail.com">Billymartinezc@gmail.com</a>
              </div>
            </div>
            <!-- Ocultar este bloque en pantallas pequeñas -->
            <div class="space-y-4 text-gray-100 hidden md:block text-lg">
              <p class="animate-fade-in">
                Soy un estudiante de Ingeniería Informática comprometido con la creación de soluciones innovadoras. Mi
                enfoque combina el uso de tecnologías emergentes y un diseño eficiente para transformar ideas en
                realidad.
              </p>
              <p class="animate-fade-in" style="animation-delay: 200ms;">
                He trabajado en proyectos como aplicaciones de banca digital y explorado realidad virtual en la
                enfermería, donde la tecnología se convierte en una herramienta clave para el progreso. Mi stack
                tecnológico incluye Vue.js, Spring, Kotlin, y despliegue en la nube con AWS y Google Cloud.
              </p>
              <p class="animate-fade-in" style="animation-delay: 400ms;">
                Actualmente, estoy explorando tecnologías como
                <magic-text-span texto-resaltar="Kotlin Multiplataforma"></magic-text-span>
                para desarrollo de aplicaciones móviles eficientes y multiplataforma. Estoy motivado a enfrentar
                desafíos que me permitan aprender y contribuir al futuro de la tecnología.
              </p>
            </div>
          </div>
          <!-- Botones con espacio reducido para pantallas pequeñas -->
          <div class="flex flex-col md:flex-row space-y-4 md:space-y-0 md:space-x-4 mt-8">
            <a
                href="https://github.com/Billyflin"
                target="_blank"
                rel="noopener noreferrer"
                class="bg-gray-700 hover:bg-gray-600 text-white font-semibold py-3 px-6 rounded-full flex items-center justify-center space-x-2 transition duration-300 shadow-lg hover:shadow-xl"
            >
              <GithubIcon class="w-5 h-5" />
              <span>Visita mi GitHub</span>
            </a>
            <a
                href="https://www.linkedin.com/in/billyflin"
                target="_blank"
                rel="noopener noreferrer"
                class="bg-gradient-to-r from-indigo-800 to-fuchsia-900 hover:bg-blue-700 text-white font-semibold py-3 px-6 rounded-full flex items-center justify-center space-x-2 transition duration-300 shadow-lg hover:shadow-xl"
            >
              <LinkedinIcon class="w-5 h-5" />
              <span>Conecta en LinkedIn</span>
            </a>
            <a
                href="https://www.instagram.com/billyfliin/"
                target="_blank"
                rel="noopener noreferrer"
                class="bg-pink-600 hover:bg-pink-700 text-white font-semibold py-3 px-6 rounded-full flex items-center justify-center space-x-2 transition duration-300 shadow-lg hover:shadow-xl"
            >
              <Instagram class="w-5 h-5" />
              <span>Instagram</span>
            </a>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { MapPinIcon, MailIcon, GithubIcon, LinkedinIcon, Instagram } from 'lucide-vue-next';
import billyflin from '../assets/img/Billyflin.jpg';
import MagicTextSpan from "./MagicTextSpan.vue";

const imageLoaded = ref(false);

const onImageLoad = () => {
  imageLoaded.value = true;
};
</script>

<style scoped>
.loader {
  width: 40px;
  height: 40px;
  border: 4px solid rgba(255, 255, 255, 0.2);
  border-top-color: #fff;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>