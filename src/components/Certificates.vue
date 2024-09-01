<template>
  <section id="certificados" class="py-20 px-6">
    <div class="container mx-auto">
      <h2 class="text-4xl font-bold text-center text-gray-100 mb-12 flex justify-center items-center">
        <GraduationCapIcon class="mr-2 h-8 w-8 text-indigo-400" />
        Mis Certificados
      </h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-10">
        <div v-for="certificate in certificates" :key="certificate.title"
             class="bg-gray-800/50 backdrop-blur-md rounded-xl shadow-lg overflow-hidden transform transition duration-300 hover:scale-105">
          <div class="p-6">
            <h3 class="font-bold text-xl mb-2 text-indigo-400 flex items-center">
              <AwardIcon class="mr-2 h-5 w-5" />
              {{ certificate.title }}
            </h3>
            <p class="text-gray-300 mb-4">{{ certificate.issuer }}</p>
            <a :href="certificate.link" target="_blank" rel="noopener noreferrer"
               class="text-indigo-400 hover:text-indigo-300 font-semibold inline-flex items-center">
              Ver certificado
              <ExternalLinkIcon class="ml-2 h-4 w-4" />
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { GraduationCapIcon, AwardIcon, ExternalLinkIcon } from 'lucide-vue-next'

defineProps({
  certificates: Array
})
</script>