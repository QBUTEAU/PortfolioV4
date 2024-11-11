<template>
  <div>
    <div v-for="project in realisations" :key="project.title" class="realisations__card">
      <div class="realisations-card__legende">
        <h3>{{ project.title }}</h3>
        <h5>{{ project.date }}</h5>
        <ul class="realisations-card__techno">
          <li v-for="tech in project.technologies" :key="tech">
            <i :class="getIconClass(tech)"></i>
          </li>
        </ul>
        <p>{{ project.description }}</p>
        <h6>
          <span v-if="project.contributors">
            Développé avec <a :href="project.contributors[0].link" target="_blank">{{ project.contributors[0].name }}</a>.<br>
            Rédactionnel et illustrations :
            <span v-for="(contributor, index) in project.contributors.slice(1)" :key="contributor.name">
              <a :href="contributor.link" target="_blank">{{ contributor.name }}</a><span v-if="index < project.contributors.length - 2"> et </span>
            </span>.
          </span>
        </h6>
      </div>
      <div :class="'realisations-card__liens ' + project.class">
        <a v-if="project.links.project" :href="project.links.project" target="_blank" style="margin-right: 35px;">
          <i class="fa-solid fa-arrow-up-right-from-square"></i>
        </a>
        <a v-if="project.links.github" :href="project.links.github" target="_blank" style="margin-left: 35px;">
          <i class="fa-brands fa-github"></i>
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import realisationsData from '@/assets/js/realisations.json';

const realisations = ref(realisationsData);

const getIconClass = (tech) => {
  if (tech === 'fa-database') {
    return 'fa-solid fa-database';
  }
  return 'fa-brands ' + tech;
};
</script>