<template>
  <section id="skills" class="mb-20">
    <h2 class="text-4xl font-bold mb-8 text-center text-gradient">Habilidades</h2>
    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-8">
      <div v-for="skill in skills" :key="skill.name"
           class="bg-gray-800 bg-opacity-50 p-6 rounded-lg shadow-lg text-center transform hover:scale-110 transition-transform duration-300">
        <component :is="skill.icon" class="w-16 h-16 mb-4 mx-auto text-blue-400"/>
        <span class="text-lg font-semibold text-gray-300">{{ skill.name }}</span>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  name: 'SkillSection',
  props: {
    skills: {
      type: Array,
      required: true
    }
  }
}
</script>
<style scoped>

@keyframes rotate {
  from {
    rotate: 0deg;
  }
  50% {
    scale: 1 1.5;
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

</style>