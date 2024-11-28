<template>
  <section id="certifications" class="py-10 md:py-20">
    <div class="container mx-auto px-4">
      <h2 class="text-4xl md:text-5xl font-bold mb-10 md:mb-16 text-center text-gradient">
        Certificaciones
      </h2>

      <!-- Certificados "grandes" -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 md:gap-8 mb-10">
        <div
            v-for="cert in certificationsWithSubcertificates"
            :key="cert.name"
            class="bg-gray-800 rounded-xl p-5 md:p-6 shadow-lg transform hover:scale-105 transition-all duration-300"
        >
          <!-- Imagen del certificado -->
          <img
              :src="cert.imageSrc"
              :alt="cert.imageAlt"
              class="w-full h-auto mb-4 rounded"
          />
          <!-- Información del certificado -->
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
          <div class="flex justify-between items-center flex-wrap mb-4">
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
          <!-- Subcertificados -->
          <div v-if="cert.subcertificates" class="pl-4 border-l border-gray-700">
            <h4 class="text-lg md:text-xl font-semibold text-white mb-2">
              Subcertificados:
            </h4>
            <ul>
              <li
                  v-for="sub in cert.subcertificates"
                  :key="sub.name"
                  class="flex items-center mb-2"
              >
                <component
                    :is="sub.icon"
                    class="w-6 h-6 md:w-8 md:h-8 mr-2 text-gradient"
                />
                <a
                    :href="sub.link"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="text-sm md:text-base text-gray-300 hover:text-white transition-colors"
                >
                  {{ sub.name }}
                </a>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Certificados "simples" -->
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6 md:gap-8">
        <div
            v-for="cert in certificationsWithoutSubcertificates"
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
import { computed } from 'vue';
import {
  LinkIcon,
  ChartPieIcon,
  DatabaseIcon,
  TrendingUpIcon,
  LayersIcon,
  BarChartIcon
} from 'lucide-vue-next';

import {
  GoogleAnalyticsIcon,
  PythonIcon,
  RIcon,
  Html5Icon,
  Css3Icon,
  AmazonWebServicesIcon,
  GoogleCloudIcon,
} from 'vue3-simple-icons';


const certifications = [
  {
    name: 'Google Advanced Data Analytics',
    description: 'Certificación de 7 cursos de análisis de datos avanzado.',
    date: 'Noviembre 2024',
    icon: GoogleAnalyticsIcon,
    imageSrc: '/CourseraGAD.png',
    imageAlt: 'Ver certificado para Billy Martinez Cofré, Google Advanced Data Analytics, ofrecido a través de Coursera. Aquellos que obtienen el Certificado de Análisis de Datos Avanzado de Google han completado siete cursos que incluyen evaluaciones prácticas y están diseñados para prepararlos para roles avanzados en análisis de datos y roles de nivel inicial en ciencia de datos. Son competentes en explorar grandes conjuntos de datos, aplicar técnicas de análisis de datos y construir modelos para extraer conocimientos. También son competentes en aprendizaje automático, modelado predictivo y estadísticas.',
    link: 'https://coursera.org/share/b44ac3af30dd271b9fc0933a3eb26f48',
    subcertificates: [
      {
        name: 'The Nuts and Bolts of Machine Learning',
        icon: LayersIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/3UNP8RK9UP6U',
      },
      {
        name: 'Regression Analysis: Simplify Complex Data Relationships',
        icon: BarChartIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/MN1LOUTBLKZ9',
      },
      {
        name: 'The Power of Statistics',
        icon: TrendingUpIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/9UPK84IDGE6O',
      },
      {
        name: 'Get Started with Python',
        icon: PythonIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/QRQ6RLJJ4MRQ',
      },
      {
        name: 'Google Advanced Data Analytics Capstone',
        icon: GoogleAnalyticsIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/P1090IV5UW1S',
      },
      {
        name: 'Go Beyond the Numbers: Translate Data into Insights',
        icon: ChartPieIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/XZXHJQPIA8LV',
      },
      {
        name: 'Foundations of Data Science',
        icon: DatabaseIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/1TYJ2507R87S',
      },
    ],
  },
  {
    name: 'Google Data Analytics',
    description: 'Certificación de 8 cursos de análisis de datos.',
    date: 'Noviembre 2024',
    icon: GoogleAnalyticsIcon,
    imageSrc: '/CourseraGD.png',
    imageAlt: 'Ver certificado para Billy Martinez Cofré, Google Data Analytics, ofrecido a través de Coursera.',
    link: 'https://coursera.org/share/cd01808e79ade1be04b6f4fa30887265',
    subcertificates: [
      {
        name: 'Data Analysis with R Programming',
        icon: RIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/U20YQ0880LMO',
      },
      {
        name: 'Process Data from Dirty to Clean',
        icon: LayersIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/REAQS9WTLELF',
      },
      {
        name: 'Foundations: Data, Data, Everywhere',
        icon: DatabaseIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/H2CU93CAVYBO',
      },
      {
        name: 'Prepare Data for Exploration',
        icon: DatabaseIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/IDVDAW7XKL1L',
      },
      {
        name: 'Google Data Analytics Capstone: Complete a Case Study',
        icon: GoogleAnalyticsIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/5UV7V8TN00X4',
      },
      {
        name: 'Analyze Data to Answer Questions',
        icon: ChartPieIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/GHVVVYNYPB3S',
      },
      {
        name: 'Share Data Through the Art of Visualization',
        icon: ChartPieIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/KXM4O3FXGZ2O',
      },
      {
        name: 'Ask Questions to Make Data-Driven Decisions',
        icon: TrendingUpIcon,
        link: 'https://www.coursera.org/account/accomplishments/verify/2PUUU22DPL4X',
      },
    ],
  },
  // Certificados simples
  {
    name: 'Codecademy - CSS',
    description: 'Uso de CSS para diseñar sitios web.',
    date: 'Agosto 2023',
    icon: Css3Icon,
    link: 'https://www.codecademy.com/profiles/Billyflin/certificates/9da84567e8ff414b91f0b23d917fb42f',
  },
  {
    name: 'Codecademy - HTML',
    description: 'Uso de HTML para estructurar sitios web.',
    date: 'Agosto 2023',
    icon: Html5Icon,
    link: 'https://www.codecademy.com/profiles/Billyflin/certificates/c6f2b55a48f440a6a876686f7487e1a7',
  },
  {
    name: 'Google Cloud Fundamentals: Core Infrastructure',
    description: 'Uso de Google Cloud para implementar aplicaciones y servicios.',
    date: 'Julio 2022',
    icon: GoogleCloudIcon,
    link: 'https://www.coursera.org/account/accomplishments/verify/KR6EN4R7CGDJ',
  },
  {
    name: 'Amazon Web Services - AWS Certified Solutions Architect',
    description: 'Diseño de sistemas distribuidos en AWS.',
    date: 'Julio 2023',
    icon: AmazonWebServicesIcon,
    link: 'https://www.youracclaim.com/users/BillyMartinezCofre/badges/ENLACE_DEL_CERTIFICADO',
  },
];

const certificationsWithSubcertificates = computed(() =>
    certifications.filter(cert => cert.subcertificates)
);

const certificationsWithoutSubcertificates = computed(() =>
    certifications.filter(cert => !cert.subcertificates)
);
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
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

.group:hover .group-hover\:animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}
</style>
