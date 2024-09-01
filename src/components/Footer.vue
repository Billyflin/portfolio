<template>
  <footer class="bg-gray-900 text-gray-300 py-12 relative overflow-hidden">
    <div class="container mx-auto px-6 text-center relative z-10">
      <h2 class="text-3xl font-bold mb-6">Conecta Conmigo</h2>
      <div class="flex justify-center space-x-6 mb-8">
        <a v-for="social in socialLinks" :key="social.name" :href="social.url" target="_blank" rel="noopener noreferrer"
           class="hover:text-indigo-400 transition duration-300 transform hover:scale-110 flex flex-col items-center">
          <component :is="social.icon" class="h-8 w-8 mb-2" />
          <span>{{ social.name }}</span>
        </a>
      </div>
      <p class="text-lg">&copy; 2023 Billy Martínez. Todos los derechos reservados.</p>
    </div>

    <!-- Chibi Anime Character -->
    <div class="absolute bottom-0 right-0 w-40 h-40 md:w-60 md:h-60 chibi-container">
      <svg viewBox="0 0 200 200" class="chibi-character">
        <!-- Cuerpo -->
        <circle cx="100" cy="120" r="60" fill="#4B5563" />

        <!-- Cabeza -->
        <circle cx="100" cy="60" r="40" fill="#9CA3AF" />

        <!-- Ojos -->
        <circle cx="85" cy="50" r="5" fill="#111827" />
        <circle cx="115" cy="50" r="5" fill="#111827" />

        <!-- Boca -->
        <path d="M90 70 Q100 80 110 70" stroke="#111827" stroke-width="2" fill="none" />

        <!-- Brazos -->
        <path d="M60 120 Q40 140 50 160" stroke="#4B5563" stroke-width="20" fill="none" />
        <path d="M140 120 Q160 140 150 160" stroke="#4B5563" stroke-width="20" fill="none" />

        <!-- Piernas -->
        <path d="M85 180 Q90 200 100 190" stroke="#4B5563" stroke-width="20" fill="none" />
        <path d="M115 180 Q110 200 100 190" stroke="#4B5563" stroke-width="20" fill="none" />
      </svg>
    </div>
  </footer>
</template>

<script setup>
import { GithubIcon, LinkedinIcon, TwitterIcon, MailIcon } from 'lucide-vue-next'

defineProps({
  socialLinks: Array
})
</script>

<style scoped>
/* Animación para el personaje chibi */
@keyframes wave {
  0%, 100% { transform: rotate(0deg); }
  25% { transform: rotate(-10deg); }
  75% { transform: rotate(10deg); }
}

.chibi-container {
  animation: wave 3s ease-in-out infinite;
  transform-origin: bottom center;
}

.chibi-character {
  width: 100%;
  height: 100%;
}
</style>