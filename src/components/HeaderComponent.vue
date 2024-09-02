<template>
  <header
      :class="['fixed top-0 left-0 right-0 z-20 transition-all duration-300',
      {'bg-gray-900 bg-opacity-90 shadow-lg': scrolled, 'bg-transparent': !scrolled}]"
  >
    <nav class="container mx-auto px-4 py-4">
      <div class="flex justify-between items-center">
        <div class="flex items-center">
          <TerminalIcon class="w-8 h-8 text-gradient mr-2 animate-pulse"/>
          <h1 class="text-2xl md:text-3xl font-bold text-gradient">Billyflin</h1>
        </div>
        <div class="hidden md:flex space-x-6">
          <a v-for="item in navItems" :key="item.href" :href="item.href"
             :class="['text-lg transition-colors', {'text-gradient text-roboto': activeSection === item.href.slice(1), 'text-gray-300 text-roboto  hover:text-amber-200': activeSection !== item.href.slice(1)}]">
            {{ item.text }}
          </a>
        </div>
        <button @click="toggleMobileMenu" class="md:hidden text-gray-300 hover:text-blue-400">
          <MenuIcon v-if="!mobileMenuOpen" class="h-6 w-6"/>
          <XIcon v-else class="h-6 w-6"/>
        </button>
      </div>
    </nav>
    <!-- Mobile Menu -->
    <transition name="slide-fade">
      <div v-if="mobileMenuOpen" class="md:hidden bg-gray-800 py-2">
        <a v-for="item in navItems" :key="item.href" :href="item.href"
           @click="closeMobileMenu"
           class="block py-2 px-4 text-gray-300 hover:bg-gray-700 hover:text-blue-400 transition-colors">
          {{ item.text }}
        </a>
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
@keyframes rotate {
  from { rotate: 0deg; }
  50% { scale: 1 1.5; }
  to { rotate: 360deg; }
}

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

.text-roboto {
  font-family: 'Roboto', sans-serif;
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: .5; }
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}
</style>