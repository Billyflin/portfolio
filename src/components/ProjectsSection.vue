<template>
  <section id="projects" class="py-20 ">
    <div class="container mx-auto px-4">
      <h2 class="text-5xl font-bold mb-16 text-center text-gradient">Proyectos</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div v-for="project in projects" :key="project.name"
             class="bg-gray-800 rounded-xl overflow-hidden shadow-lg transform hover:scale-105 transition-all duration-300 flex flex-col">
          <div class="relative h-56 overflow-hidden">
            <img :src="project.image" :alt="project.name" class="w-full h-full object-cover transition-transform duration-300 hover:scale-110"/>
            <div class="absolute inset-0 bg-gradient-to-t from-gray-900 to-transparent opacity-60"></div>
          </div>
          <div class="p-6 flex-grow">
            <h3 class="text-2xl font-semibold mb-3 text-gradient">{{ project.name }}</h3>
            <p class="text-gray-300 mb-4">{{ project.description }}</p>
            <div class="mb-4">
              <h4 class="text-sm font-semibold text-gray-400 mb-2">Tecnologías utilizadas:</h4>
              <div class="flex flex-wrap gap-2">
                <span v-for="tech in project.technologies" :key="tech"
                      class="px-2 py-1 bg-gray-700 text-gray-300 text-xs rounded-full">
                  {{ tech }}
                </span>
              </div>
            </div>
          </div>
          <div class="p-6 pt-0 flex space-x-4">
            <a :href="project.github" target="_blank" rel="noopener noreferrer"
               class="flex-1 bg-gray-700 hover:bg-gray-600 text-white px-4 py-2 rounded-md transition-colors flex items-center justify-center group">
              <GitHubIcon class="w-5 h-5 mr-2 group-hover:animate-pulse"/>
              GitHub
            </a>
            <a :href="project.demo" target="_blank" rel="noopener noreferrer"
               class="flex-1 bg-purple-600 hover:bg-purple-500 text-white px-4 py-2 rounded-md transition-colors flex items-center justify-center group">
              <LinkIcon class="w-5 h-5 mr-2 group-hover:animate-pulse"/>
              Demo
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { GitHubIcon } from "vue3-simple-icons";
import { LinkIcon } from 'lucide-vue-next';

defineProps({
  projects: {
    type: Array,
    required: true,
    validator: (value) => {
      return value.every(project =>
          project.name &&
          project.description &&
          project.image &&
          project.github &&
          project.demo &&
          Array.isArray(project.technologies)
      );
    }
  }
});
</script>

<style scoped>
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

.group:hover .group-hover\:animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}
</style>