<template>
  <section id="skills" class="py-20 ">
    <div class="container mx-auto px-4">
      <h2 class="text-5xl font-bold mb-16 text-center text-gradient">Mis Habilidades</h2>
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
        <div v-for="category in skillCategories" :key="category.name"
             class="bg-gray-800 bg-opacity-90 rounded-xl p-8 shadow-lg backdrop-blur-sm transform hover:scale-105 transition-all duration-300">
          <h3 class="text-3xl font-semibold mb-6 text-white border-b border-gray-700 pb-2">{{ category.name }}</h3>
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-6">
            <div v-for="skill in category.skills" :key="skill.name"
                 class="flex flex-col items-center p-4 bg-gray-700 bg-opacity-50 rounded-lg hover:bg-opacity-70 transition-all duration-300">
              <component :is="skill.icon" class="w-12 h-12 mb-3 text-gradient skill-icon"/>
              <span class="text-sm font-medium text-white text-center">{{ skill.name }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';
import {
  AmazonWebServicesIcon,
  ArduinoIcon,
  CPlusPlusIcon,
  DockerIcon,
  FirebaseIcon,
  GitIcon,
  GoogleCloudIcon,
  JavaScriptIcon,
  KotlinIcon,
  MongoDbIcon,
  NodeDotjsIcon,
  PythonIcon,
  ReactIcon,
  RocketIcon,
  SpringBootIcon,
  SpringIcon,
  TypeScriptIcon,
  VueDotjsIcon
} from 'vue3-simple-icons';

const skillCategories = ref([
  {
    name: 'Lenguajes de Programación',
    skills: [
      {name: 'JavaScript', icon: JavaScriptIcon},
      {name: 'TypeScript', icon: TypeScriptIcon},
      {name: 'Python', icon: PythonIcon},
      {name: 'Java', icon: SpringBootIcon},
      {name: 'Kotlin', icon: KotlinIcon},
      {name: 'C++', icon: CPlusPlusIcon},
      {name: 'Arduino', icon: ArduinoIcon},
    ]
  },
  {
    name: 'Frameworks y Librerías',
    skills: [
      {name: 'Vue.js', icon: VueDotjsIcon},
      {name: 'React', icon: ReactIcon},
      {name: 'Node.js', icon: NodeDotjsIcon},
      {name: 'Spring', icon: SpringIcon},
    ]
  },
  {
    name: 'Bases de Datos y Cloud',
    skills: [
      {name: 'MongoDB', icon: MongoDbIcon},
      {name: 'Firebase', icon: FirebaseIcon},
      {name: 'AWS', icon: AmazonWebServicesIcon},
      {name: 'Google Cloud', icon: GoogleCloudIcon},
    ]
  },
  {
    name: 'Herramientas y Tecnologías',
    skills: [
      {name: 'Docker', icon: DockerIcon},
      {name: 'Git', icon: GitIcon},
      {name: 'CI/CD', icon: RocketIcon},
      {name: 'Arduino', icon: ArduinoIcon},
    ]
  },
]);
</script>

<style scoped>
@keyframes background-pan {
  from {
    background-position: 0% center;
  }
  to {
    background-position: -200% center;
  }
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

.skill-icon {
  transition: all 0.3s ease;
}

.skill-icon:hover {
  filter: drop-shadow(0 0 0.75rem currentColor);
}

@keyframes float {
  0% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
  100% {
    transform: translateY(0px);
  }
}

.flex:hover .skill-icon {
  animation: float 3s ease-in-out infinite;
}
</style>