<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-900 via-gray-800 to-gray-900 text-gray-100">
    <Header :navItems="navItems" />
    <Hero @showAboutMe="showAboutMe = true" />
    <Projects :projects="projects" />
    <Skills :skills="skills" />
    <Certificates :certificates="certificates" />
    <Footer :socialLinks="socialLinks" />
    <AboutMeModal v-if="showAboutMe" @close="showAboutMe = false" />
  </div>



</template>

<script setup>
import { ref } from 'vue'
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import Projects from './components/Projects.vue'
import Skills from './components/Skills.vue'
import Certificates from './components/Certificates.vue'
import Footer from './components/Footer.vue'
import AboutMeModal from './components/AboutMeModal.vue'
import ufroSustentable from './assets/img/logoUfroSustentable.svg'
import happLogo from './assets/img/LogoHapp.svg'

import {
  CodeIcon, FolderIcon, AwardIcon, GraduationCapIcon, HomeIcon, CloudIcon,
  DatabaseIcon, BoxIcon, GitBranchIcon, SmartphoneIcon, ServerIcon,
  BrainCircuitIcon, LockIcon, CpuIcon, SproutIcon, GithubIcon, LinkedinIcon, TwitterIcon, MailIcon
} from 'lucide-vue-next'

const showAboutMe = ref(false)

const navItems = [
  { name: 'Inicio', icon: HomeIcon },
  { name: 'Proyectos', icon: FolderIcon },
  { name: 'Habilidades', icon: AwardIcon },
  { name: 'Certificados', icon: GraduationCapIcon }
]

const projects = [
  {
    title: 'Ufro Sustentable',
    description: 'App para Android e iOS, que utiliza IA para clasificar residuos y promover el reciclaje en la comunidad.',
    image: ufroSustentable,
    link: 'https://www.linkedin.com/feed/update/urn:li:activity:7216289603790532608/',
    icon: SproutIcon,
    technologies: ['Kotlin Multiplatform', 'Swift', 'Firebase',  'Google Maps', 'Jetpack Compose', 'Material Design']
  },
  {
    title: 'Sistema de Gestión de Propiedades',
    description: 'Software de gestión de arriendos con funcionalidades de IA para predicción de precios y mantenimiento preventivo.',
    image: happLogo,
    link: '#',
    icon: HomeIcon,
    technologies: ['React', 'Node.js', 'MongoDB', 'TensorFlow.js', 'Google Cloud']
  },

]

const skills = [
  { name: 'Vue.js', icon: CodeIcon },
  { name: 'Spring Boot', icon: ServerIcon },
  { name: 'Node.js', icon: ServerIcon },
  { name: 'Kotlin', icon: SmartphoneIcon },
  { name: 'Python', icon: CodeIcon },
  { name: 'Java', icon: CpuIcon },
  { name: 'AWS', icon: CloudIcon },
  { name: 'Google Cloud', icon: CloudIcon },
  { name: 'Docker', icon: BoxIcon },
  { name: 'Kubernetes', icon: BoxIcon },
  { name: 'MongoDB', icon: DatabaseIcon },
  { name: 'PostgreSQL', icon: DatabaseIcon },
  { name: 'CI/CD', icon: GitBranchIcon },
  { name: 'TensorFlow', icon: BrainCircuitIcon },
  { name: 'REST APIs', icon: ServerIcon },
  { name: 'Microservicios', icon: ServerIcon },
  { name: 'Git', icon: GitBranchIcon },
  { name: 'Seguridad Web', icon: LockIcon }
]

const certificates = [
  {
    title: 'Learn Python 3',
    issuer: 'Codecademy',
    link: 'https://www.codecademy.com/profiles/Billyflin/certificates/9da84567e8ff414b91f0b23d917fb42f'
  },
  {
    title: 'Google Cloud Infrastructure',
    issuer: 'Coursera',
    link: 'https://www.coursera.org/account/accomplishments/verify/5SQ5CZ3ZD48K'
  },
  {
    title: 'Google Cloud Platform Fundamentals',
    issuer: 'Coursera',
    link: 'https://www.coursera.org/account/accomplishments/verify/KR6EN4R7CGDJ'
  },
]

const socialLinks = [
  { name: 'GitHub', icon: GithubIcon, url: '#' },
  { name: 'LinkedIn', icon: LinkedinIcon, url: '#' },
  { name: 'Twitter', icon: TwitterIcon, url: '#' },
  { name: 'Email', icon: MailIcon, url: 'mailto:tu@email.com' }
]
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');

</style>