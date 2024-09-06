<script setup>
  import { ref, onMounted } from 'vue';
  import './assets/js/script.js';
  // import Competences from './components/Competences.vue';
  import Realisations from './components/Realisations.vue';
  import AutresRealisations from './components/AutresRealisations.vue';
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
        <h6>Développeur Front-End Junior</h6>
        <ul class="presentation__reseaux">
          <li><a href="https://github.com/QBUTEAU" target="_blank"><i class="fa-brands fa-github"></i></a>
          </li>
          <li><a href="https://www.linkedin.com/in/quentin-buteau/" target="_blank"><i
                class="fa-brands fa-linkedin"></i></a></li>
          <li><a href="http://qbuteau.fr/link" target="_blank"><i class="fa-solid fa-link"></i></a></li>
        </ul>
      </div>
      <!-- <a href="#apropos"><i class="fa-solid fa-arrow-down" style="color: #fff; font-size: 35px;"></i></a> -->
    </div>

    <div id="apropos">
      <div class="apropos__contenu">
        <h2>À propos de moi</h2>
        <p>Bienvenue sur mon portfolio ! Je suis Quentin, j'ai 19 ans et je suis en troisième
          année d'un BUT Métiers du Multimédia et de l'Internet au sein de l'IUT de Troyes.
          Ma passion pour le développement web a débuté au lycée, où j'ai pu découvrir les
          langages HTML, CSS et SQL en cours de spécialité Numériques et Sciences Informatiques
          pendant de mon Baccalauréat Général.
          Je suis actuellement à la recherche d'une alternance dans le développement web, d'une durée
          d'un an, à compter de septembre 2024.
          Je suis également passionné par le sport, la photo, le cinéma et les sports mécaniques.
        </p>
        <ul class="cv">
          <li><a href="http://qbuteau.fr/ressources/QBUTEAU_CV.pdf" target="_blank">MON CV</a></li>
          <li><a href="http://qbuteau.fr/ressources/QBUTEAU_CV-N&B.pdf" target="_blank">MON CV - N&B</a></li>
        </ul>
      </div>
      <div class="apropos__photo">
      </div>
    </div>

    <Competences />

    <div id="realisations">
      <h2>Mes réalisations</h2>
      <Realisations />
    </div>


    <div class="autres-realisations">
      <h2>Autres Réalisations</h2>
        <AutresRealisations />
    </div>

    <div id="travaux_mmi" class="travaux_mmi">
      <h2>MES TRAVAUX EN BUT MMI</h2>
      <p>Portfolios universitaires (.pdf)</p>
      <div>
        <a class="liens_travaux" href="http://qbuteau.fr/portfolio/QBUTEAU_BUT1.pdf" target="_blank">B.U.T.1 (S1
          & S2)</a>
        <a class="liens_travaux" href="http://qbuteau.fr/portfolio/QBUTEAU_BUT2.pdf" target="_blank">B.U.T.2 (S3
          & S4)</a>
      </div>
      <p>Modules de Développement Front / Intégration</p>
      <ul class="travaux-mmi__modules">
        <li><a class="liens_travaux" href="http://mmi22c03.mmi-troyes.fr/travaux/r112" target="_blank">WR112</a>
        </li>
        <li><a class="liens_travaux" href="http://mmi22c03.mmi-troyes.fr/travaux/r212" target="_blank">WR212</a>
        </li>
        <li><a class="liens_travaux" href="http://mmi22c03.mmi-troyes.fr/travaux/r312" target="_blank">WR312</a>
        </li>
        <li><a class="liens_travaux" href="http://mmi22c03.mmi-troyes.fr/travaux/r312sass" target="_blank">WR312
            (SCSS)</a></li>
      </ul>
    </div>
  </section>

  <footer>
    <div id="copyright">&copy; 2023-2024 - Quentin BUTEAU</div>
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
        <a onclick="copierTexte()" class="reseaux" id="discord">
          <i class="fa-brands fa-discord"></i>
        </a>
      </li>
      <li>
        <a href="https://www.behance.net/quentinbuteau" target="_blank" class="reseaux">
          <i class="fa-brands fa-behance"></i>
        </a>
      </li>
    </ul>
  </footer>

  <!-- POP UP DE CTRL C CTRL V DU DISCORD -->
  <div id="copy-popup">
    L'ID Discord de Quentin a été copié avec succès !
  </div>

</template>


<style scoped></style>