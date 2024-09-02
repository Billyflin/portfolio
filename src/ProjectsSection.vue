<template>
  <section id="projects" class="mb-20">
    <h2 class="text-4xl font-bold mb-8 text-center text-gradient">Proyectos</h2>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
      <div v-for="project in projects" :key="project.name"
           class="bg-gray-800 bg-opacity-50 rounded-lg overflow-hidden shadow-lg transform hover:scale-105 transition-transform duration-300">
        <img :src="project.image" :alt="project.name" class="w-full h-48 object-cover"/>
        <div class="p-6">
          <h3 class="text-2xl font-semibold mb-2 text-blue-400">{{ project.name }}</h3>
          <p class="text-gray-400 mb-4">{{ project.description }}</p>
          <div class="flex space-x-4">
            <a :href="project.github" target="_blank" rel="noopener noreferrer"
               class="bg-gray-700 hover:bg-gray-600 text-white px-4 py-2 rounded-md transition-colors flex items-center">
              <GitHubIcon class="w-5 h-5 mr-2"/>
              GitHub
            </a>
            <a :href="project.demo" target="_blank" rel="noopener noreferrer"
               class="bg-blue-600 hover:bg-blue-500 text-white px-4 py-2 rounded-md transition-colors flex items-center">
              <LinkIcon class="w-5 h-5 mr-2"/>
              Demo en vivo
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<script setup>
import { GitHubIcon } from "vue3-simple-icons";
import { LinkIcon} from 'lucide-vue-next';

defineProps({
  projects: Array
});
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