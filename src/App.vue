<template>
  <div id="app">
    <header>
      <nav>
        <ul>
          <li><a href="#about">À propos</a></li>
          <li><a href="#projects">Projets</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
      </nav>
    </header>

    <section id="hero">
      <div class="hero-content">
        <div id="typewriter" class="typed-text"></div>
        <p>Découvrez mes projets et compétences</p>
      </div>
    </section>

    <section id="about">
      <div class="about-content">
        <h2>À propos de moi</h2>
        <div class="about-info">
          <img src="./assets/memoji_sanscorps.png" alt="Avatar" class="profile-image">
          <p>Bonjour 👋🏼 ! Je m'appelle <strong>Guillaume Zimol</strong> et je suis actuellement en Master Informatique à la Faculté des Sciences de Nancy.<br>
            Passionné par les nouvelles technologies, j'apprécie particulièrement <br> le <strong>développement</strong> front-end et back-end, le tennis 🎾 la natation 🏊🏼‍ et l'astronomie 🔭.<br>
            À travers ce portfolio, je vous présente les <strong>projets</strong> que j'ai réalisés, les <strong>technologies</strong> que je maîtrise et mes <strong>coordonnées</strong> de contact.
          </p>
        </div>
      </div>
    </section>

    <section id="projects">
      <h2 class="titre">Mes projets</h2>
      <div class="project-grid">
        <project-item v-for="project in projects" :key="project.id" :project="project" @open-project-modal="openProjectModal" >
           <!-- Pour passer des components dans des components <p>blabla</p> -->
        </project-item>
      </div>
    </section>

    <div v-if="showProjectModal" class="project-modal">
      <div class="modal-content">
        <h3>{{ selectedProject.title }}</h3>
        <p>{{ selectedProject.description }}</p>
        <!-- Ajoutez ici d'autres détails spécifiques au projet -->
        <button @click="closeProjectModal">Fermer</button>
      </div>
    </div>




    <section id="contact">
      <h2 class="titre">Contactez-moi</h2>
      <div class="contact-links">
        <div class="social-icon-container">
          <a href="mailto:guillaume.test@gmail.com">
            <img src="./assets/gmail.png" alt="E-mail" class="social-icon email-icon">
          </a>
        </div>
        <div class="social-icon-container">
          <a href="https://www.linkedin.com/in/guillaume-zimol-12b36617b" target="_blank" rel="noopener noreferrer">
            <img src="./assets/linkedin.png" alt="LinkedIn" class="social-icon linkedin-icon">
          </a>
        </div>
        <div class="social-icon-container">
          <a href="https://github.com/Stalh" target="_blank" rel="noopener noreferrer">
            <img src="./assets/github.png" alt="GitHub" class="social-icon github-icon">
          </a>
        </div>
      </div>
    </section>



    <footer>
      <p>&copy; Made by Guillaume Zimol</p>
    </footer>
  </div>
</template>

<script setup>
import {onMounted, ref} from 'vue';
import ProjectItem from './components/ProjectItem.vue';
import Typewriter from 'typewriter-effect/dist/core';

const projects = ref([
  {
    id: 1,
    image: require('./assets/test.png'),
    title: 'Projet 1',
    summary: 'Résumé du projet 1',
    description: 'Description détaillée du projet 1'
  },
  {
    id: 2,
    image: require('./assets/test.png'),
    title: 'Projet 2',
    summary: 'Résumé du projet 2',
    description: 'Description détaillée du projet 2'
  },
  {
    id: 3,
    image: require('./assets/test.png'),
    title: 'Projet 3',
    summary: 'Résumé du projet 3',
    description: 'Description détaillée du projet 3'
  },
]);

const selectedProject = ref(null);
const showProjectModal = ref(false);

const openProjectModal = (project) => {
  selectedProject.value = project;
  showProjectModal.value = true;
};

const closeProjectModal = () => {
  selectedProject.value = null;
  showProjectModal.value = false;
};

onMounted(() => {
  new Typewriter('#typewriter', {
    strings: ['GuillaumZ', 'Guillaume Zimol - Développeur Web'],
    autoStart: true,
    loop: true
  });
});

</script>

