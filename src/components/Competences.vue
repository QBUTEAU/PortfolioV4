<template>
    <div id="competences">
        <h2>Mes compétences</h2>
        <div v-for="category in competences" :key="category.category" class="competences__liste">
            <p>{{ category.category }}</p>
            <ul>
                <li v-for="skill in category.skills" :key="skill.name">
                    <i :class="skill.iconClass" :style="{ color: skill.color }" v-if="skill.iconClass"></i>
                    <span :class="{ 'no-margin': category.category === 'Autres outils' }">{{ skill.name }}</span>
                </li>
            </ul>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import competencesData from '@/assets/js/competences.json';

const competences = ref(competencesData);
</script>

<style scoped>
.no-margin {
    margin-left: 0 !important;
}
</style>