<template>
  <div>
    <div v-for="project in realisations" :key="project.title" class="realisations__card">
      <div class="realisations-card__legende">
        <h3>{{ project.title }}</h3>
        <h5>{{ project.date }}</h5>
        <ul class="realisations-card__techno">
          <li v-for="tech in project.technologies" :key="tech">
            <span class="tech-badge">{{ tech }}</span>
          </li>
        </ul>
        <p>{{ project.description }}</p>
        <h6 v-if="project.contributors">
          <span>
            Partie Intégration faite par <a :href="project.contributors[0].link" target="_blank">{{ project.contributors[0].name
              }}</a>.<br>
            Rédactionnel et illustrations :
            <span v-for="(contributor, index) in project.contributors.slice(1)" :key="contributor.name">
              <a :href="contributor.link" target="_blank">{{ contributor.name }}</a><span
                v-if="index < project.contributors.length - 2"> et </span>
            </span>.
          </span>
        </h6>
      </div>
      <div :class="'realisations-card__liens ' + project.class">
        <a v-if="project.links && project.links.project" :href="project.links.project" target="_blank">
          <i class="fa-solid fa-arrow-up-right-from-square"></i>
        </a>
        <a v-if="project.links && project.links.github" :href="project.links.github" target="_blank">
          <i class="fa-brands fa-github"></i>
        </a>
        <a v-if="project.links && project.links.behance" :href="project.links.behance" target="_blank">
          <i class="fa-brands fa-behance-square"></i>
        </a>
        <a v-if="project.links && project.links.figma" :href="project.links.figma" target="_blank">
          <i class="fa-brands fa-figma"></i>
        </a>
        <a v-if="project.links && project.links.link" :href="project.links.link"
          style="color: #F9F9F9; font-weight: 500; font-size: 20px;">
          c.f. Stage B.U.T.3
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import realisationsData from '@/assets/js/realisations.json';

const realisations = ref(realisationsData);
</script>
