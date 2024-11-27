<template>
  <section id="certifications" class="py-10 md:py-20">
    <div class="container mx-auto px-4">
      <h2 class="text-4xl md:text-5xl font-bold mb-10 md:mb-16 text-center text-gradient">
        Certificaciones
      </h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-2 lg:grid-cols-3 gap-6 md:gap-8">
        <div
            v-for="cert in certifications"
            :key="cert.name"
            class="bg-gray-800 rounded-xl p-5 md:p-6 shadow-lg transform hover:scale-105 transition-all duration-300"
        >
          <div class="flex items-center mb-3 md:mb-4">
            <component
                :is="cert.icon"
                class="w-10 h-10 md:w-12 md:h-12 mr-3 md:mr-4 text-gradient"
            />
            <h3 class="text-xl md:text-2xl font-semibold text-white">
              {{ cert.name }}
            </h3>
          </div>
          <p class="text-gray-300 mb-3 md:mb-4 text-sm md:text-base">
            {{ cert.description }}
          </p>
          <div class="flex justify-between items-center flex-wrap">
            <span class="text-xs md:text-sm text-gray-400">
              {{ cert.date }}
            </span>
            <a
                :href="cert.link"
                target="_blank"
                rel="noopener noreferrer"
                class="bg-purple-600 hover:bg-purple-500 text-white px-3 py-2 md:px-4 md:py-2 rounded-md transition-colors flex items-center group"
            >
              <LinkIcon class="w-4 h-4 md:w-5 md:h-5 mr-1 md:mr-2 group-hover:animate-pulse" />
              <span class="text-xs md:text-sm">Ver certificado</span>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>


<script setup>
import { ServerIcon,LinkIcon } from 'lucide-vue-next';
import {Amazonec2Icon, Css3Icon, GoogleDataflowIcon, Html5Icon} from "vue3-simple-icons";

const certifications = [
  {
    name:'Google Data Analytics: Ask Questions to Make Data-Driven Decisions',
    description: 'Certificación que valida la capacidad de hacer preguntas y tomar decisiones basadas en datos.',
    date: 'Noviembre 2024',
    icon: GoogleDataflowIcon,
    link: 'https://coursera.org/share/4f455dc94f1d7dcdb508f641b9cd20ad'
  },
  {name: 'Google Data Analytics: Data, Data, Everywhere',
    description: 'Certificación que valida la capacidad de analizar datos y tomar decisiones basadas en ellos.',
    date: 'Noviembre 2024',
    icon: GoogleDataflowIcon,
    lin: 'https://coursera.org/share/a27620eae606cf00581ab24eb97ecf59'

  }
    ,
  {
    name: 'Codecademy - CSS',
    description: 'Certificación que valida la capacidad de usar CSS para diseñar sitios web.',
    date: 'Agosto 2023',
    icon: Css3Icon,
    link: 'https://www.codecademy.com/profiles/Billyflin/certificates/9da84567e8ff414b91f0b23d917fb42f'
  },  {
    name: 'Codecademy - HTML',
    description: 'Certificación que valida la capacidad de usar HTML para diseñar sitios web.',
    date: 'Agosto 2023',
    icon: Html5Icon,
    link: 'https://www.codecademy.com/profiles/Billyflin/certificates/c6f2b55a48f440a6a876686f7487e1a7'
  },
  {
    name: 'Google Cloud Fundamentals: Core Infrastructure',
    description: 'Certificación que valida la capacidad de usar Google Cloud para implementar aplicaciones y servicios.',
    date: 'Julio 2022',
    icon: ServerIcon,
    link: 'https://www.coursera.org/account/accomplishments/verify/KR6EN4R7CGDJ'
  },
  {
    name: 'Google Cloud Infrastructure: Foundation',
    description: 'Acreditación que valida la capacidad de usar Google Cloud para implementar aplicaciones y servicios.',
    date: 'Julio 2022',
    icon: ServerIcon,
    link: 'https://www.coursera.org/account/accomplishments/verify/5SQ5CZ3ZD48K'
  },
  {
    name: 'Amazon Web Services - AWS Certified Solutions Architect',
    description: 'Certificación que valida la capacidad de diseñar sistemas distribuidos en AWS.',
    date: 'Julio 2023',
    icon: Amazonec2Icon,
    link: ''
  }
];
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

@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: .5;
  }
}

.group:hover .group-hover\:animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}
</style>