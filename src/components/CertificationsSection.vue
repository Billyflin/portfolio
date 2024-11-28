<template>
  <section id="certifications" class="py-16">
    <div class="container mx-auto px-6">
      <h2 class="text-4xl font-bold mb-12 text-center text-gradient">
        Certificaciones
      </h2>

      <!-- Certificados "grandes" -->
      <div class="space-y-12 mb-16">
        <div
            v-for="cert in certificationsWithSubcertificates"
            :key="cert.name"
            class="bg-gray-800 rounded-lg shadow-lg p-6 flex flex-col md:flex-row items-stretch md:items-start"
        >
          <!-- Imagen del certificado y de la insignia -->
          <div class="md:w-1/3 mb-6 md:mb-0 flex flex-col items-center">
            <img
                :src="cert.imageSrc"
                :alt="cert.imageAlt"
                class="w-full h-auto rounded-lg shadow-md"
            />
            <!-- Imagen de la insignia -->
            <div v-if="cert.badgeImg" class="mt-4">
              <a
                  :href="cert.badge"
                  target="_blank"
                  rel="noopener noreferrer"
              >
                <img
                    :src="cert.badgeImg"
                    :alt="cert.badgeAlt"
                    class="max-w-xs h-auto mx-auto"
                />
              </a>
            </div>
          </div>

          <!-- Información del certificado -->
          <div class="md:w-2/3 md:pl-8">
            <div class="flex items-center mb-4">
              <component
                  :is="cert.icon"
                  class="w-12 h-12 mr-4 text-white"
              />
              <h3 class="text-3xl font-semibold text-white">
                {{ cert.name }}
              </h3>
            </div>
            <p class="text-gray-300 mb-4">
              {{ cert.description }}
            </p>
            <!-- Habilidades -->
            <div class="flex flex-wrap mb-4">
              <span
                  v-for="skill in cert.skills"
                  :key="skill"
                  class="bg-purple-600 text-white text-sm font-medium mr-2 mb-2 px-3 py-1 rounded-full"
              >
                {{ skill }}
              </span>
            </div>
            <div class="flex justify-between items-center mb-4">
              <div class="flex items-center text-gray-400">
                <CalendarIcon class="w-5 h-5 mr-2" />
                <span>{{ cert.date }}</span>
              </div>
              <a
                  :href="cert.link"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="text-purple-500 hover:text-purple-400 transition-colors flex items-center"
              >
                <ExternalLinkIcon class="w-5 h-5 mr-1" />
                <span>Ver certificado</span>
              </a>
            </div>
            <!-- Subcertificados -->
            <div v-if="cert.subcertificates" class="mt-6">
              <h4 class="text-2xl font-semibold text-white mb-3">
                Subcertificados
              </h4>
              <ul class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                <li
                    v-for="sub in cert.subcertificates"
                    :key="sub.name"
                    class="flex items-center bg-gray-700 rounded-lg p-4"
                >
                  <component
                      :is="sub.icon"
                      class="w-6 h-6 mr-3 text-white"
                  />
                  <a
                      :href="sub.link"
                      target="_blank"
                      rel="noopener noreferrer"
                      class="text-gray-300 hover:text-white transition-colors"
                  >
                    {{ sub.name }}
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>

      <!-- Certificados "simples" -->
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-8">
        <div
            v-for="cert in certificationsWithoutSubcertificates"
            :key="cert.name"
            class="bg-gray-800 rounded-lg shadow-lg p-6"
        >
          <div class="flex items-center mb-4">
            <component
                :is="cert.icon"
                class="w-10 h-10 mr-3 text-white"
            />
            <h3 class="text-2xl font-semibold text-white">
              {{ cert.name }}
            </h3>
          </div>
          <p class="text-gray-300 mb-4">
            {{ cert.description }}
          </p>
          <!-- Habilidades -->
          <div v-if="cert.skills" class="flex flex-wrap mb-4">
            <span
                v-for="skill in cert.skills"
                :key="skill"
                class="bg-purple-600 text-white text-sm font-medium mr-2 mb-2 px-3 py-1 rounded-full"
            >
              {{ skill }}
            </span>
          </div>
          <div class="flex justify-between items-center mb-4">
            <div class="flex items-center text-gray-400">
              <CalendarIcon class="w-5 h-5 mr-2" />
              <span>{{ cert.date }}</span>
            </div>
            <a
                :href="cert.link"
                target="_blank"
                rel="noopener noreferrer"
                class="text-purple-500 hover:text-purple-400 transition-colors flex items-center"
            >
              <ExternalLinkIcon class="w-5 h-5 mr-1" />
              <span>Ver certificado</span>
            </a>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>


<script setup>
import {computed} from 'vue';
import {
  LinkIcon,
  CalendarIcon,
  ExternalLinkIcon,
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
    description:
        'Programa profesional que abarca 7 cursos enfocados en análisis de datos avanzado. Este certificado valida habilidades en ciencia de datos, aprendizaje automático, análisis estadístico y programación en Python. Los graduados son competentes en explorar grandes conjuntos de datos, aplicar técnicas de análisis avanzadas y construir modelos predictivos para extraer insights valiosos.',
    date: 'Noviembre 2024',
    icon: GoogleAnalyticsIcon,
    imageSrc: '/CourseraGAD.png',
    imageAlt: 'Ver certificado para Billy Martinez Cofré, Google Advanced Data Analytics, ofrecido a través de Coursera. Aquellos que obtienen el Certificado de Análisis de Datos Avanzado de Google han completado siete cursos que incluyen evaluaciones prácticas y están diseñados para prepararlos para roles avanzados en análisis de datos y roles de nivel inicial en ciencia de datos. Son competentes en explorar grandes conjuntos de datos, aplicar técnicas de análisis de datos y construir modelos para extraer conocimientos. También son competentes en aprendizaje automático, modelado predictivo y estadísticas.',
    link: 'https://coursera.org/share/b44ac3af30dd271b9fc0933a3eb26f48',
    badge: 'https://www.credly.com/badges/d8079709-e5f5-404f-84b1-fdf90366e698/public_url',
    badgeAlt: 'Ver insignia de Credly para Billy Martinez Cofré, Google Advanced Data Analytics, ofrecido a través de Coursera.',
    badgeImg: '/google-advanced-data-analytics-certificate.png',
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
    skills: [
      'Data Science',
      'Data Analysis',
      'Python Programming',
      'Jupyter Notebook',
      'Machine Learning',
      'Statistical Analysis',
      'Tableau Software',
      'Data Visualization',
      'Predictive Modelling',
      'Kaggle',
      'Exploratory Data Analysis (EDA)',
      'Regression Models'
    ],
  },
  {
    name: 'Google Data Analytics',
    skills: [
      'Data Analysis',
      'Data Cleaning',
      'Data Visualization',
      'Spreadsheets',
      'SQL',
      'R Programming',
      'Data Collection',
      'Statistical Analysis',
      'Data Ethics',
      'Data-driven Decision Making',
      'Problem Solving',
      'Critical Thinking',
      'Data Interpretation',
      'Communication Skills',
    ],
    description: 'Certificado profesional que comprende 8 cursos diseñados para proporcionar habilidades esenciales en análisis de datos. Este programa capacita en el manejo de datos, limpieza, análisis y visualización, utilizando herramientas como R, SQL y hojas de cálculo. Los graduados están preparados para roles de analista de datos de nivel inicial, capaces de tomar decisiones basadas en datos y comunicar resultados de manera efectiva.',
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
    badge: 'https://www.credly.com/badges/ab1b6b6d-f85f-4aff-9b93-480a149550e8/public_url',
    badgeAlt: 'Ver insignia de Credly para Billy Martinez Cofré, Google Data Analytics Professional Certificate, ofrecido a través de Coursera.',
    badgeImg: '/google-data-analytics-professional-certificate.2.png',

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
