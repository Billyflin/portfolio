<template>
  <section id="habilidades" class="py-20 px-6 bg-gray-800/30">
    <div class="container mx-auto">
      <h2 class="text-4xl font-bold text-center text-gray-100 mb-12 flex justify-center items-center">
        <AwardIcon class="mr-2 h-8 w-8 text-indigo-400" />
        Mis Habilidades
      </h2>
      <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-6 gap-6">
        <div v-for="skill in skills" :key="skill.name"
             class="bg-gray-800/50 backdrop-blur-md rounded-xl shadow-lg p-4 flex flex-col items-center justify-center transition duration-300 hover:bg-gray-700/50">
          <component :is="skill.icon" class="h-8 w-8 text-indigo-400 mb-2"/>
          <span class="text-sm font-semibold text-gray-300 text-center">{{ skill.name }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import {AwardIcon} from 'lucide-vue-next'

defineProps({
  skills: Array
})
</script>