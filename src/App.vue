<template>
  <div class="relative min-h-screen overflow-hidden bg-gray-900 text-gray-100 z-0">
    <!-- Blob Background -->
    <div ref="blob" class="blob"></div>
    <div class="blur"></div>

    <!-- Main Content -->
    <div class="relative z-2">
      <!-- Header -->
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
                 :class="['text-lg transition-colors', {'text-blue-400': activeSection === item.href.slice(1), 'text-gray-300 hover:text-blue-400': activeSection !== item.href.slice(1)}]">
                {{ item.text }}
              </a>
            </div>
            <button @click="toggleMobileMenu" class="md:hidden text-gray-300 hover:text-blue-400">
              <MenuIcon v-if="!mobileMenuOpen" class="h-6 w-6" />
              <XIcon v-else class="h-6 w-6" />
            </button>
          </div>
        </nav>
        <!-- Mobile Menu -->
        <transition name="slide-fade">
          <div v-if="mobileMenuOpen" class="md:hidden bg-gray-800 py-2">
            <a v-for="item in navItems" :key="item.href" :href="item.href"
               @click="mobileMenuOpen = false"
               class="block py-2 px-4 text-gray-300 hover:bg-gray-700 hover:text-blue-400 transition-colors">
              {{ item.text }}
            </a>
          </div>
        </transition>
      </header>

      <!-- Hero Section -->
      <Hero />

      <!-- Main Content -->
      <main class="container mx-auto px-4 py-16">
        <!-- About Section -->
        <AboutSection/>

        <!-- Skills Section -->
        <SkillSection :skills="skills"/>

        <!-- Projects Section -->
        <ProjectsSection :projects="projects"/>

        <!-- Contact Section -->
        <ContactSection :socialLinks="socialLinks"/>
      </main>

      <!-- Footer -->
      <footer class="bg-gray-800 bg-opacity-50 py-8">
        <div class="container mx-auto px-4 text-center text-gray-400">
          <p>&copy; {{ new Date().getFullYear() }} Billyflin. Todos los derechos reservados. Como si fuera mi primera pag web jajaja</p>
        </div>
      </footer>
    </div>
  </div>
</template>

<script setup>
import {onMounted, onUnmounted, ref} from 'vue';
import {
  GitHubIcon,
  GmailIcon,
  InstagramIcon,
  JavaScriptIcon,
  LinkedInIcon,
  NodeDotjsIcon,
  PythonIcon,
  ReactIcon,
  TypeScriptIcon,
  VueDotjsIcon
} from 'vue3-simple-icons';
import {MenuIcon, TerminalIcon, XIcon} from "lucide-vue-next";
import Hero from "./components/Hero.vue";
import ContactSection from "./ContactSection.vue";
import ProjectsSection from "./ProjectsSection.vue";
import SkillSection from "./SkillSection.vue";
import AboutSection from "./AboutSection.vue";

const blob = ref(null);
const scrolled = ref(false);
const mobileMenuOpen = ref(false);
const activeSection = ref('');

const navItems = [
  { href: '#about', text: 'Acerca de mí' },
  { href: '#skills', text: 'Habilidades' },
  { href: '#projects', text: 'Proyectos' },
  { href: '#contact', text: 'Contacto' },
];

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value;
};

const handleScroll = () => {
  scrolled.value = window.scrollY > 50;

  const sections = ['contact', 'projects', 'skills', 'about'];
  for (const section of sections) {
    const element = document.getElementById(section);
    if (element && window.scrollY >= element.offsetTop - 100) {
      activeSection.value = section;
      break;
    }
  }
};

onMounted(() => {
  if (blob.value) {
    window.onpointermove = event => {
      const { clientX, clientY } = event;

      blob.value.animate({
        left: `${clientX}px`,
        top: `${clientY}px`
      }, { duration: 3000, fill: "forwards" });
    }
  }

  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});

const skills = [
  { name: 'Vue.js', icon: VueDotjsIcon },
  { name: 'React', icon: ReactIcon },
  { name: 'JavaScript', icon: JavaScriptIcon },
  { name: 'TypeScript', icon: TypeScriptIcon },
  { name: 'Node.js', icon: NodeDotjsIcon },
  { name: 'Python', icon: PythonIcon },
];

const projects = [
  {
    name: 'Plataforma E-commerce',
    description: 'Una solución de comercio electrónico full-stack construida con Vue.js y Node.js.',
    image: '/placeholder.svg?height=300&width=400',
    github: 'https://github.com/billy-martinez/ecommerce',
    demo: 'https://ecommerce-demo.com',
  },
  {
    name: 'App de Gestión de Tareas',
    description: 'Una aplicación de gestión de tareas basada en React con una interfaz de usuario limpia.',
    image: '/placeholder.svg?height=300&width=400',
    github: 'https://github.com/billy-martinez/task-manager',
    demo: 'https://task-manager-demo.com',
  },
  {
    name: 'Dashboard del Clima',
    description: 'Un dashboard del clima utilizando Vue.js y una API de terceros.',
    image: '/placeholder.svg?height=300&width=400',
    github: 'https://github.com/billy-martinez/weather-dashboard',
    demo: 'https://weather-dashboard-demo.com',
  },
];

const socialLinks = [
  { name: 'LinkedIn', icon: LinkedInIcon, url: 'https://www.linkedin.com/in/billy-martinez', bgClass: 'bg-blue-600 hover:bg-blue-700' },
  { name: 'GitHub', icon: GitHubIcon, url: 'https://github.com/billy-martinez', bgClass: 'bg-gray-700 hover:bg-gray-800' },
  { name: 'Instagram', icon: InstagramIcon, url: 'https://www.instagram.com/billy.martinez', bgClass: 'bg-pink-600 hover:bg-pink-700' },
  { name: 'Email', icon: GmailIcon, url: 'mailto:billy.martinez@example.com', bgClass: 'bg-red-600 hover:bg-red-700' },
];
</script>

<style scoped>

@keyframes rotate {
  from { rotate: 0deg; }
  50% { scale: 1 1.5; }
  to { rotate: 360deg; }
}

@keyframes background-pan {
  from {
    background-position: 0% center;
  }

  to {
    background-position: -200% center;
  }
}

.font-roboto{
  font-family: "Roboto", sans-serif;
}

.blob {
  height: 20vmax;
  aspect-ratio: 1;
  position: fixed;
  z-index: -3;
  left: 50%;
  top: 50%;
  translate: -50% -50%;
  border-radius: 50%;
  background: linear-gradient(
      to right,
      rgb(123, 31, 162),
      rgb(103, 58, 183),
      rgb(244, 143, 177),
      rgb(123, 31, 162)
  );
  animation: rotate 20s infinite;
  opacity: 0.8;
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

.blur {
  height: 100%;
  width: 100%;
  position: absolute;
  z-index: -2;
  backdrop-filter: blur(11vmax);
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: .5; }
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}
</style>