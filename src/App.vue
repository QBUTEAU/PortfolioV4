<script setup>
import { ref, onMounted } from 'vue';
import './assets/js/script.js';
import Parcours from './components/Parcours.vue';
import Competences from './components/Competences.vue';
import Realisations from './components/Realisations.vue';
import AutresRealisations from './components/AutresRealisations.vue';

const showPdf = ref(false);
const pdfUrl = ref('');

function openPdf(file) {
  // Utilise import.meta.url pour charger depuis assets (Vite)
  pdfUrl.value = new URL(`./assets/portfolios/${file}`, import.meta.url).href;
  showPdf.value = true;
}
function closePdf() {
  showPdf.value = false;
  pdfUrl.value = '';
}
</script>


<template>

  <header id="navbar">
    <a class="navbar__logo" href="">QBUTEAU</a>
    <label for="toggle"><i id="icon" class="fa-solid fa-bars"></i></label>
    <input type="checkbox" id="toggle">
    <ul class="navbar__liens">
      <li><a href="#apropos">À propos de moi</a></li>
      <li><a href="#competences">Mes compétences</a></li>
      <li><a href="#realisations">Mes réalisations</a></li>
    </ul>
  </header>

  <section>

    <!-- FLECHE POUR REMONTER EN HAUT DE PAGE -->
    <a href="#presentation" id="backToTop" class="hidden">
      <div>
        <i class="fa-solid fa-arrow-up"></i>
      </div>
    </a>

    <div id="presentation">
      <div class="presentation__nom-role">
        <h1>Quentin BUTEAU</h1>
        <h6>Développeur Full-Stack Junior</h6>
      </div>
      <!-- <a href="#apropos"><i class="fa-solid fa-arrow-down" style="color: #fff; font-size: 35px;"></i></a> -->
    </div>


    <h2>À propos de moi</h2>

    <div id="apropos">
      <div class="apropos__contenu">
        <h3>Qui suis-je ?</h3>
        <p>Je m'appelle Quentin, j'ai 20 ans et je suis fraîchement diplômé du BUT Métiers du Multimédia et de l'Internet, 
          obtenu à l'IUT de Troyes. Ma passion pour le développement web a débuté au lycée, lors de la découverte des langages 
          HTML, CSS et SQL dans le cadre de la spécialité Numérique et Sciences Informatiques de mon Baccalauréat Général. Au cours 
          de ma formation, j'ai acquis des compétences solides en développement web, design, audiovisuel et gestion de projets 
          numériques, me permettant d'adopter une approche polyvalente et complète dans mes réalisations. Je suis également passionné
          par le sport, la photographie, le cinéma ainsi que les sports mécaniques.
        </p>
        <div class="apropos-contenu__skills">
          <span>Organisé</span>
          <span>Curieux</span>
          <span>Autonome</span>
          <span>Esprit d'équipe</span>
        </div>
      </div>
      <div class="apropos__photo">
      </div>
    </div>

    <Parcours />

    <Competences />

    <div id="realisations">
      <h2>Mes réalisations</h2>
      <Realisations />
    </div>


    <!-- <div class="autres-realisations">
      <h2>Autres Réalisations</h2>
      <AutresRealisations />
    </div> -->

    <div id="travaux_mmi" class="travaux_mmi">
      <h2>MES TRAVAUX EN BUT MMI</h2>
      <p>Portfolios universitaires (.pdf)</p>
      <div>
        <button class="liens_travaux" @click="openPdf('QBUTEAU_BUT1.pdf')">B.U.T.1</button>
        <button class="liens_travaux" @click="openPdf('QBUTEAU_BUT2.pdf')">B.U.T.2</button>
        <button class="liens_travaux" @click="openPdf('QBUTEAU_BUT3.pdf')">B.U.T.3</button>
      </div>
      <p>Soutenances de stage (.pdf)</p>
      <div>
        <button class="liens_travaux" @click="openPdf('QBUTEAU_StageBUT2.pdf')">Stage B.U.T.2</button>
        <button class="liens_travaux" @click="openPdf('QBUTEAU_StageBUT3.pdf')">Stage B.U.T.3</button>
      </div>
    </div>
  </section>

  <footer>
    <div id="copyright">&copy; 2023-2025 - Quentin BUTEAU</div>
    <ul id="liens-contact">
      <li>
        <a href="mailto:buteauquentin10@gmail.com" target="_blank" class="reseaux">
          <i class="fa-solid fa-envelope"></i>
        </a>
      </li>
      <li>
        <a href="https://instagram.com/quentin.bto" target="_blank" class="reseaux">
          <i class="fa-brands fa-instagram"></i>
        </a>
      </li>
      <li>
        <a href="https://www.linkedin.com/in/quentin-buteau/" target="_blank" class="reseaux">
          <i class="fa-brands fa-linkedin"></i>
        </a>
      </li>
      <li>
        <a href="https://github.com/QBUTEAU" target="_blank" class="reseaux">
          <i class="fa-brands fa-github"></i>
        </a>
      </li>
      <li>
        <a href="https://www.behance.net/quentinbuteau" target="_blank" class="reseaux">
          <i class="fa-brands fa-behance"></i>
        </a>
      </li>
    </ul>
  </footer>

  <!-- Popup PDF -->
  <div v-if="showPdf" class="pdf-popup" @click.self="closePdf">
    <button class="pdf-popup__close" @click="closePdf">&times;</button>
    <div class="pdf-popup__content">
      <iframe :src="pdfUrl" width="800" height="600"></iframe>
    </div>
  </div>

</template>


<style scoped>
.pdf-popup {
  position: fixed;
  z-index: 1000;
  inset: 0;
  background: rgba(30,30,30,0.95);
  display: flex;
  align-items: center;
  justify-content: center;
}
.pdf-popup__content {
  position: relative;
  background: #222;
  border-radius: 12px;
  padding: 24px 24px 12px 24px;
  box-shadow: 0 2px 16px #000a;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.pdf-popup__close {
  position: fixed;
  top: 32px;
  right: 48px;
  background: none;
  border: none;
  color: #fff;
  font-size: 2.5em;
  cursor: pointer;
  z-index: 1100;
  transition: color 0.2s;
}
.pdf-popup__close:hover {
  color: #C0392B;
}
.pdf-popup iframe {
  border: none;
  border-radius: 8px;
  background: #fff;
  max-width: 90vw;
  max-height: 80vh;
}
@media (max-width: 900px) {
  .pdf-popup iframe {
    width: 95vw;
    height: 60vh;
  }
  .pdf-popup__content {
    padding: 10px 2px 2px 2px;
  }
  .pdf-popup__close {
    top: 12px;
    right: 18px;
    font-size: 2em;
  }
}
</style>