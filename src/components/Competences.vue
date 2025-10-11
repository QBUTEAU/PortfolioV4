<template>
  <div id="competences">
    <h2>Mes compétences</h2>
    <div class="competences__container">
      <div
        v-for="category in competences"
        :key="category.category"
        class="competences__bloc"
      >
        <h3>{{ category.category }}</h3>
        <ul>
          <li v-for="skill in category.skills" :key="skill.name">
            {{ skill.name }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import competencesData from '@/assets/js/competences.json';

const competences = ref(competencesData);
</script>
