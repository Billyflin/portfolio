<template>
  <div class="relative min-h-screen overflow-hidden bg-gray-900 text-gray-100">
    <!-- Blob Background -->
    <div ref="blob" class="blob"></div>
    <div class="blur"></div>

    <!-- Existing Content -->
    <div class="relative z-10">
      <!-- Header -->
      <header
          :class="['fixed top-0 left-0 right-0 z-20 transition-all duration-300', {'bg-gray-900 shadow-lg': scrolled, 'bg-transparent': !scrolled}]">
        <nav class="container mx-auto px-4 py-4">
          <div class="flex justify-between items-center">
            <div class="flex items-center">
              <TerminalIcon class="w-8 h-8 md:w-8 md:h-8 text-gradient mr-2"/>
              <h1 class="text-2xl md:text-3xl font-bold text-gradient">Billyflin</h1>
            </div>
            <div class="hidden md:flex space-x-6">
              <a v-for="item in navItems" :key="item.href" :href="item.href"
                 :class="['text-lg transition-colors', {'text-blue-400': activeSection === item.href.slice(1), 'text-gray-300 hover:text-blue-400': activeSection !== item.href.slice(1)}]">
                {{ item.text }}
              </a>
            </div>
            <button @click="toggleMobileMenu" class="md:hidden text-gray-300 hover:text-blue-400">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
                   stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"/>
              </svg>
            </button>
          </div>
        </nav>
        <!-- Mobile Menu -->
        <div v-if="mobileMenuOpen" class="md:hidden bg-gray-800 py-2">
          <a v-for="item in navItems" :key="item.href" :href="item.href"
             @click="mobileMenuOpen = false"
             class="block py-2 px-4 text-gray-300 hover:bg-gray-700 hover:text-blue-400">
            {{ item.text }}
          </a>
        </div>
      </header>

      <!-- Hero Section -->
      <Hero/>

      <!-- Main Content -->
      <main class="container mx-auto px-4 py-16">
        <!-- About Section -->
        <section id="about" class="mb-20">
          <h2 class="text-4xl font-bold mb-8 text-center text-blue-400">Acerca de mí</h2>
          <div class="bg-gray-800 p-8 rounded-lg shadow-lg transform hover:scale-105 transition-transform duration-300">
            <p class="text-gray-300 text-lg leading-relaxed">
              Soy un apasionado desarrollador full-stack y estudiante de Ingeniería Informática.
              Me encanta resolver problemas complejos y aprender nuevas tecnologías.
              Mi objetivo es construir aplicaciones eficientes, escalables y amigables para el usuario
              que generen un impacto positivo en la sociedad.
            </p>
          </div>
        </section>

        <!-- Skills Section -->
        <section id="skills" class="mb-20">
          <h2 class="text-4xl font-bold mb-8 text-center text-blue-400">Habilidades</h2>
          <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-8">
            <div v-for="skill in skills" :key="skill.name"
                 class="bg-gray-800 p-6 rounded-lg shadow-lg text-center transform hover:scale-110 transition-transform duration-300">
              <component :is="skill.icon" class="w-16 h-16 mb-4 mx-auto text-blue-400"/>
              <span class="text-lg font-semibold text-gray-300">{{ skill.name }}</span>
            </div>
          </div>
        </section>

        <!-- Projects Section -->
        <section id="projects" class="mb-20">
          <h2 class="text-4xl font-bold mb-8 text-center text-blue-400">Proyectos</h2>
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <div v-for="project in projects" :key="project.name"
                 class="bg-gray-800 rounded-lg overflow-hidden shadow-lg transform hover:scale-105 transition-transform duration-300">
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

        <!-- Contact Section -->
        <section id="contact" class="mb-20">
          <h2 class="text-4xl font-bold mb-8 text-center text-blue-400">Contáctame</h2>
          <div class="flex flex-wrap justify-center gap-6">
            <a href="https://www.linkedin.com/in/billy-martinez" target="_blank" rel="noopener noreferrer"
               class="flex items-center bg-blue-600 text-white px-6 py-3 rounded-full hover:bg-blue-500 transition-colors">
              <LinkedInIcon class="w-6 h-6 mr-2"/>
              <span>LinkedIn</span>
            </a>
            <a href="https://github.com/billy-martinez" target="_blank" rel="noopener noreferrer"
               class="flex items-center bg-gray-700 text-white px-6 py-3 rounded-full hover:bg-gray-600 transition-colors">
              <GitHubIcon class="w-6 h-6 mr-2"/>
              <span>GitHub</span>
            </a>
            <a href="https://www.instagram.com/billy.martinez" target="_blank" rel="noopener noreferrer"
               class="flex items-center bg-pink-600 text-white px-6 py-3 rounded-full hover:bg-pink-500 transition-colors">
              <InstagramIcon class="w-6 h-6 mr-2"/>
              <span>Instagram</span>
            </a>
            <a href="mailto:billy.martinez@example.com"
               class="flex items-center bg-red-600 text-white px-6 py-3 rounded-full hover:bg-red-500 transition-colors">
              <GmailIcon class="w-6 h-6 mr-2"/>
              <span>Envíame un correo</span>
            </a>
          </div>
        </section>
      </main>

      <!-- Footer -->
      <footer class="bg-gray-800 py-8">
        <div class="container mx-auto px-4 text-center text-gray-400">
          <p>&copy; 2023 Billy Martínez. Todos los derechos reservados.</p>
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
import {LinkIcon, TerminalIcon} from "lucide-vue-next";
import Hero from "./Hero.vue";

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

  // Determine active section
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
</script>

<style scoped>
@keyframes rotate {
  from {
    rotate: 0deg;
  }

  50% {
    scale: 1 1.7;
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

.blob {
  height: 20vmax;
  aspect-ratio: 1;
  position: absolute;
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
  font-weight: normal;
  font-family: "Rubik", sans-serif;
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
  z-index: 2;
  backdrop-filter: blur(11vmax);
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>