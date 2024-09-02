<template>
  <div class="relative min-h-screen overflow-hidden bg-gray-900 text-gray-100">
    <!-- Blob Background -->
    <div ref="blob" class="blob"></div>
    <div class="blur"></div>

    <!-- Main Content -->
    <div class="relative z-10">
      <!-- Header -->
      <HeaderComponent
          :nav-items="navItems"
          :scrolled="scrolled"
          :active-section="activeSection"
          @update:active-section="updateActiveSection"
      />

      <!-- Hero Section -->
      <Hero />

      <!-- Main Content -->
      <main class="container mx-auto px-4 py-16">
        <!-- About Section -->
        <AboutSection />

        <!-- Skills Section -->
        <SkillSection :skills="skills" />

        <!-- Projects Section -->
        <ProjectsSection :projects="projects" />

        <!-- Contact Section -->
        <ContactSection :social-links="socialLinks" />
      </main>

      <!-- Footer -->
      <FooterComponent />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
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
import Hero from "./components/Hero.vue";
import ContactSection from "./components/ContactSection.vue";
import ProjectsSection from "./components/ProjectsSection.vue";
import SkillSection from "./components/SkillSection.vue";
import AboutSection from "./components/AboutSection.vue";
import FooterComponent from "./components/FooterComponent.vue";
import HeaderComponent from "./components/HeaderComponent.vue";

const blob = ref(null);
const scrolled = ref(false);
const activeSection = ref('');

const navItems = [
  { href: '#about', text: 'Acerca de mí' },
  { href: '#skills', text: 'Habilidades' },
  { href: '#projects', text: 'Proyectos' },
  { href: '#contact', text: 'Contacto' },
];

const updateActiveSection = (section) => {
  activeSection.value = section;
};

const handleScroll = () => {
  scrolled.value = window.scrollY > 50;

  const sections = ['contact', 'projects', 'skills', 'about'];
  for (const section of sections) {
    const element = document.getElementById(section);
    if (element && window.scrollY >= element.offsetTop - 100) {
      updateActiveSection(section);
      break;
    }
  }
};

const handleBlobAnimation = (event) => {
  const { clientX, clientY } = event;
  blob.value.animate({
    left: `${clientX}px`,
    top: `${clientY}px`
  }, { duration: 3000, fill: "forwards" });
};

onMounted(() => {
  if (blob.value) {
    window.addEventListener('pointermove', handleBlobAnimation);
  }
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('pointermove', handleBlobAnimation);
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
  { name: 'LinkedIn', icon: LinkedInIcon, url: 'https://www.linkedin.com/in/billyflin', bgClass: 'bg-blue-600 hover:bg-blue-700' },
  { name: 'GitHub', icon: GitHubIcon, url: 'https://github.com/Billyflin', bgClass: 'bg-gray-700 hover:bg-gray-800' },
  { name: 'Instagram', icon: InstagramIcon, url: 'https://www.instagram.com/billyfliin/', bgClass: 'bg-pink-600 hover:bg-pink-700' },
  { name: 'Email', icon: GmailIcon, url: 'mailto:billymartinezc@gmail.com', bgClass: 'bg-red-600 hover:bg-red-700' },
];
</script>

<style scoped>
@keyframes rotate {
  from { rotate: 0deg; }
  50% { scale: 1 1.5; }
  to { rotate: 360deg; }
}

.blob {
  height: 20vmax;
  aspect-ratio: 1;
  position: fixed;
  z-index: 1;
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

.blur {
  height: 100%;
  width: 100%;
  position: fixed;
  z-index: 2;
  backdrop-filter: blur(11vmax);
}
</style>