<template>
  <div class="school">
    <h3 class="school__h3">Mon parcours</h3>
    <div class="school__carousel">
      <button
        class="carousel-arrow left"
        @click="prev"
        :disabled="startIndex === 0"
      >
        &lt;
      </button>
      <div class="school__list">
        <div
          class="school-list__contenu"
          v-for="etape in visibleParcours"
          :key="etape.title"
        >
          <h3>{{ etape.title }}</h3>
          <p>{{ etape.location }}</p>
          <h5>{{ etape.date }}</h5>
          <p>{{ etape.desc }}</p>
        </div>
      </div>
      <button
        class="carousel-arrow right"
        @click="next"
        :disabled="startIndex >= parcours.length - maxVisible"
      >
        &gt;
      </button>
    </div>
    <div class="carousel-dots">
      <span
        v-for="i in totalPages"
        :key="i"
        :class="['dot', { active: i - 1 === currentPage }]"
      ></span>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue';
import parcoursData from '@/assets/js/parcours.json';

const parcours = ref(parcoursData);
const startIndex = ref(0);
const maxVisible = ref(3);

const updateMaxVisible = () => {
  maxVisible.value = window.innerWidth <= 900 ? 1 : 3;
  if (startIndex.value > parcours.value.length - maxVisible.value) {
    startIndex.value = Math.max(0, parcours.value.length - maxVisible.value);
  }
};

onMounted(() => {
  updateMaxVisible();
  window.addEventListener('resize', updateMaxVisible);
});

const endIndex = computed(() => startIndex.value + maxVisible.value);

const visibleParcours = computed(() =>
  parcours.value.slice(startIndex.value, endIndex.value)
);

// Le nombre de "pages" = nombre de positions possibles de la fenêtre glissante
const totalPages = computed(() =>
  Math.max(1, parcours.value.length - maxVisible.value + 1)
);
const currentPage = computed(() => startIndex.value);

function prev() {
  if (startIndex.value > 0) startIndex.value--;
}
function next() {
  if (startIndex.value < parcours.value.length - maxVisible.value) startIndex.value++;
}
</script>

<style scoped>
.carousel-dots {
  display: flex;
  justify-content: center;
  margin-top: 18px;
  gap: 8px;
}
.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: #bbb;
  display: inline-block;
  transition: background 0.3s;
}
.dot.active {
  background: #C0392B;
}
</style>
