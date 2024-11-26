<template>
  <header
      :class="['fixed top-0 left-0 right-0 z-20 transition-all duration-300',
      {'bg-gray-900 bg-opacity-90 shadow-lg': scrolled, 'bg-transparent': !scrolled}]"
  >
    <nav class="container mx-auto px-4 py-4">
      <div class="flex justify-between items-center">
        <!-- Logo -->
        <div class="flex items-center">
          <TerminalIcon class="w-8 h-8 text-gradient mr-2 animate-pulse"/>
          <h1 class="text-2xl md:text-3xl font-bold text-gradient hover:scale-105 transition-transform">Billyflin</h1>
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex space-x-6">
          <a v-for="item in navItems" :key="item.href" :href="item.href"
             :class="['relative text-lg transition-colors group',
                      {'text-gradient font-semibold': activeSection === item.href.slice(1),
                       'text-gray-300 hover:text-amber-200': activeSection !== item.href.slice(1)}]">
            {{ item.text }}
            <!-- Underline animation -->
            <span v-if="activeSection === item.href.slice(1)" class="absolute bottom-0 left-0 w-full h-0.5 bg-gradient-to-r from-purple-500 to-pink-500 transform scale-x-0 group-hover:scale-x-100 transition-transform origin-left"></span>
          </a>
        </div>

        <!-- Mobile Menu Button -->
        <button @click="toggleMobileMenu" class="md:hidden text-gray-300 hover:text-blue-400">
          <MenuIcon v-if="!mobileMenuOpen" class="h-6 w-6"/>
          <XIcon v-else class="h-6 w-6"/>
        </button>
      </div>
    </nav>

    <!-- Mobile Menu -->
    <transition name="slide-fade">
      <div v-if="mobileMenuOpen" class="md:hidden bg-gray-900 py-4 px-4 absolute top-0 left-0 right-0 h-screen">
        <div class="flex flex-col items-center space-y-6">
          <a v-for="item in navItems" :key="item.href" :href="item.href"
             @click="closeMobileMenu"
             class="block text-xl text-gray-300 hover:bg-gray-700 hover:text-indigo-400 px-6 py-3 rounded-lg transition-colors w-full text-center">
            {{ item.text }}
          </a>
        </div>
      </div>
    </transition>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import { TerminalIcon, MenuIcon, XIcon } from 'lucide-vue-next';

const props = defineProps({
  navItems: {
    type: Array,
    required: true
  }
});

const emit = defineEmits(['update:activeSection']);

const scrolled = ref(false);
const mobileMenuOpen = ref(false);
const activeSection = ref('');

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value;
};

const closeMobileMenu = () => {
  mobileMenuOpen.value = false;
};

const handleScroll = () => {
  scrolled.value = window.scrollY > 50;

  const sections = ['contact', 'projects', 'skills', 'about'];
  for (const section of sections) {
    const element = document.getElementById(section);
    if (element && window.scrollY >= element.offsetTop - 100) {
      activeSection.value = section;
      emit('update:activeSection', section);
      break;
    }
  }
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<style scoped>
@keyframes background-pan {
  from { background-position: 0% center; }
  to { background-position: -200% center; }
}

.text-gradient {
  animation: background-pan 3s linear infinite;
  font-family: "Roboto", sans-serif;
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

.group:hover .text-gradient {
  background: linear-gradient(to right, rgb(255, 99, 71), rgb(255, 140, 0));
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.3s ease;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(-10px);
  opacity: 0;
}
</style>
