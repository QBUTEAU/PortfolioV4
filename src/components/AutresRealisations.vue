<template>
  <div class="autresList">
    <div v-for="project in autresRealisations" :key="project.title" class="autresCard">
      <div :class="'autresCard__img ' + project.imgClass">
        <div class="autresCard-img__fond">
          <a v-for="link in project.links" :key="link.url" :href="link.url" target="_blank">
            <i :class="link.iconClass"></i>
          </a>
        </div>
      </div>
      <div class="autresCard__legende">
        <h4>{{ project.title }}</h4>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import autresRealisationsData from '@/assets/js/autres-realisations.json';

const autresRealisations = ref(autresRealisationsData);
</script>
