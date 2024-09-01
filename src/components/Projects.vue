<template>
  <section id="proyectos" class="py-20 px-6">
    <div class="container mx-auto">
      <h2 class="text-4xl font-bold text-center text-gray-100 mb-12 flex justify-center items-center">
        <FolderIcon class="mr-2 h-8 w-8 text-indigo-400" />
        Mis Proyectos
      </h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-10">
        <div v-for="project in projects" :key="project.title"
             class="bg-gray-800/50 backdrop-blur-md rounded-xl shadow-lg overflow-hidden transform transition duration-300">
          <img :src="project.image" :alt="project.title" class="w-full h-56 object-contain p-6">
          <div class="p-6">
            <h3 class="font-bold text-xl mb-2 text-indigo-400 flex items-center">
              <component :is="project.icon" class="mr-2 h-5 w-5" />
              {{ project.title }}
            </h3>
            <p class="text-gray-300 mb-4">{{ project.description }}</p>
            <div class="mb-4">
              <h4 class="text-sm font-semibold text-gray-400 mb-2">Tecnologías utilizadas:</h4>
              <div class="flex flex-wrap gap-2">
                <span v-for="tech in project.technologies" :key="tech"
                      class="bg-gray-700 text-gray-300 px-2 py-1 rounded-full text-xs">
                  {{ tech }}
                </span>
              </div>
            </div>
            <a :href="project.link" target="_blank" rel="noopener noreferrer"
               class="text-indigo-400 hover:text-indigo-300 font-semibold inline-flex items-center">
              Ver proyecto
              <ArrowRightIcon class="ml-2 h-4 w-4" />
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { FolderIcon, ArrowRightIcon } from 'lucide-vue-next'

defineProps({
  projects: Array
})
</script>