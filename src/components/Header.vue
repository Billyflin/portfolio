<template>
  <header class="fixed w-full z-50 transition-all duration-300" :class="{'bg-gray-800/70 backdrop-blur-md shadow-md': scrolled, 'bg-transparent': !scrolled}">
    <nav class="container mx-auto px-6 py-4">
      <div class="flex justify-between items-center">
        <div class="text-2xl font-bold text-indigo-400 flex items-center">
          <CodeIcon class="mr-2" />
          BM
        </div>
        <div class="hidden md:flex space-x-6">
          <a v-for="item in navItems" :key="item.name" :href="`#${item.name.toLowerCase()}`" class="text-gray-300 hover:text-indigo-400 transition duration-300 flex items-center">
            <component :is="item.icon" class="mr-1 h-5 w-5" />
            {{ item.name }}
          </a>
        </div>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { CodeIcon } from 'lucide-vue-next'

const props = defineProps({
  navItems: Array
})

const scrolled = ref(false)

const handleScroll = () => {
  scrolled.value = window.scrollY > 50
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>