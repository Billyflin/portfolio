<template>
  <div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
    <div class="bg-gray-800 rounded-lg p-8 max-w-2xl mx-4 relative text-gray-300">
      <button @click="$emit('close')" class="absolute top-4 right-4 text-gray-400 hover:text-gray-200">
        <XIcon class="h-6 w-6" />
      </button>
      <h2 class="text-3xl font-bold mb-4 text-indigo-400">Sobre Mí</h2>
      <p class="mb-4">
        Soy Billy Martínez, estudiante de 4to año de Ingeniería Informática en la Universidad de la Frontera. Apasionado por la tecnología, he adquirido experiencia en desarrollo de software e investigación en realidad virtual. He trabajado en proyectos reales, reforzando mis habilidades técnicas y capacidad para trabajar en equipo.
      </p>
      <p class="mb-4">
        Participé en un proyecto de investigación en realidad virtual con el Decanato de Enfermería de mi universidad. También trabajé en el desarrollo de una aplicación para un banco digital y colaboré con una empresa de arriendos para desarrollar su software interno.
      </p>
      <p class="mb-4">
        Tengo experiencia en Vue.js, Pinia, Spring, Kotlin, y en la integración de Spring Security y JWT en proyectos. He desplegado aplicaciones utilizando AWS y Google Cloud, y trabajado con bases de datos como MongoDB en Atlas, Firebase, y las bases de datos gestionadas por AWS.
      </p>
      <p class="mb-4">
        Poseo experiencia en varios lenguajes de programación como Java, JavaScript, PHP, Python y C++. He trabajado con Arduino para desarrollar un interruptor remoto. Tengo un conocimiento profundo de GitHub y GitLab, y he trabajado en el desarrollo de pipelines de CI/CD. También tengo experiencia en la dockerización de aplicaciones.
      </p>
      <p>
        He utilizado Kotlin para desarrollar aplicaciones de Android y actualmente estoy aprendiendo a usar Kotlin Multiplataforma para desarrollar aplicaciones para iOS y Android con el mismo código. Estoy emocionado por las oportunidades que me esperan después de graduarme y estoy abierto a roles de pasantías o de tiempo completo donde pueda seguir creciendo y aprendiendo.
      </p>
    </div>
  </div>
</template>

<script setup>
import { XIcon } from 'lucide-vue-next'

defineEmits(['close'])
</script>