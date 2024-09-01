<template>
  <section id="inicio" class="pt-32 pb-20 px-6">
    <div class="container mx-auto text-center">
      <h1 class="text-5xl md:text-7xl font-extrabold mb-4 bg-clip-text text-transparent bg-gradient-to-r from-indigo-400 to-pink-400">
        Hola, soy Billy Martínez
      </h1>
      <p class="text-xl md:text-2xl mb-8 text-gray-300 flex justify-center items-center">
        <CodeIcon class="mr-2 h-6 w-6 text-indigo-400" />
        Estudiante de Ingeniería Informática y Desarrollador Full Stack
      </p>
      <div class="flex justify-center space-x-4">
        <a href="#proyectos" class="bg-indigo-600 text-white font-bold py-3 px-8 rounded-full hover:bg-indigo-700 transition duration-300 transform hover:scale-105 flex items-center">
          <FolderIcon class="mr-2 h-5 w-5" />
          Ver Proyectos
        </a>
        <button @click="$emit('showAboutMe')" class="bg-pink-600 text-white font-bold py-3 px-8 rounded-full hover:bg-pink-700 transition duration-300 transform hover:scale-105 flex items-center">
          <UserIcon class="mr-2 h-5 w-5" />
          Sobre Mí
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { CodeIcon, FolderIcon, UserIcon } from 'lucide-vue-next'

defineEmits(['showAboutMe'])
</script>