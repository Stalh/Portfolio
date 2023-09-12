<template>
  <body>
  <div id="app">
    <header>
      <nav>
        <ul>
          <li><a href="#about">À propos</a></li>
          <li><a href="#projects">Projets</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
      </nav>
      <!-- <button @click="darkMode = !darkMode">Mode sombre</button> -->
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
        <project-item v-for="project in projects" :key="project.id" :project="project" @click="openProjectModal(project)">
          <!-- Pour passer des components dans des components <p>blabla</p> -->
        </project-item>
      </div>
    </section>

    <div v-if="showProjectModal" class="project-modal">
      <div class="modal-content">
        <div class="project-image-modal">
          <img :src="selectedProject.image2" alt="Image du projet">
        </div>
        <div class="project-details">
          <div class="project-summary">
            <h3>{{ selectedProject.title }}</h3>
            <p>{{ selectedProject.summary }}</p>
          </div>
          <div class="project-description">
            <h4>Description détaillée :</h4>
            <p>{{ selectedProject.description }}</p>
          </div>
          <div class="technologies">
            <hr class="modal-line">
            <h4>Technologies utilisées :</h4>
            <div class="technology-logos">
          <span v-for="technology in selectedProject.technologies" :key="technology.name" class="technology-logo">
            <img :src="technology.icon" alt="Icone {{ technology.name }}">
          </span>
            </div>
          </div>
        </div>
        <button @click="closeProjectModal">Fermer</button>
      </div>
    </div>


    <!-- Section représentant une frise chronologique de mon parcours scolaire et de mes expériences professionnelles -->
    <section id="parcours">
      <h2>Expériences et parcours</h2>
      <ul class="timeline">
        <li>
          <div class="direction-l">
            <div class="flag-wrapper">
              <span class="flag">Lycée Louis Bertrand</span>
              <span class="time-wrapper"><span class="time">2015 - 2018</span></span>
            </div>
            <div class="desc">BAC S SI spécialité ISN. <br>  </div>
          </div>
        </li>
        <li>
          <div class="direction-r">
            <div class="flag-wrapper">
              <span class="flag">FST (Nancy)</span>
              <span class="time-wrapper"><span class="time">2018 - 2022</span></span>
            </div>
            <div class="desc">Au cours de ma Licence j'ai réalisé de nombreux </div>
          </div>
        </li>
        <li>
          <div class="direction-l">
            <div class="flag-wrapper">
              <span class="flag">Proximus</span>
              <span class="time-wrapper"><span class="time">2022 (Avril - Juin)</span></span>
            </div>
            <div class="desc">Stage en informatique en tant que développeur web.</div>
          </div>
        </li>
        <li>
          <div class="direction-r">
            <div class="flag-wrapper">
              <span class="flag">FST (Nancy)</span>
              <span class="time-wrapper"><span class="time">2022 - 2023</span></span>
            </div>
            <div class="desc">Première année de Master Informatique général, renforcement de mon analyse algorithmique et réalisation de nombreux projets.</div>
          </div>
        </li>
        <li>
          <div class="direction-l">
            <div class="flag-wrapper">
              <span class="flag">FST (Nancy</span>
              <span class="time-wrapper"><span class="time">2023 - </span></span>
            </div>
            <div class="desc">Deuxième année de Master Informatique spécialisé en Ingénierie Logiciel.</div>
          </div>
        </li>
      </ul>
    </section>


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
        <a href="./assets/CV.pdf" download="Cv_Guillaume_Zimol.pdf">
          <img src="./assets/cv.png" alt="CV" class="social-icon cv-icon">
        </a>
      </div>
    </section>



    <footer>
      <p>&copy; Made by Guillaume Zimol</p>
    </footer>
  </div>
  </body>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import ProjectItem from './components/ProjectItem.vue';
import Typewriter from 'typewriter-effect/dist/core';
import Sparticles from 'sparticles';

import gppitIcon from './assets/gppit_icon.png';
import gppit from './assets/gppit.png';
import git from './assets/git.png';
import js from './assets/js.png';
import php from './assets/php.png';
import composer from './assets/composer.png';
import mysql from './assets/mysql.png';
import figma from './assets/figma.png';
import slim from './assets/slim.png';
import dpiscineIcon from './assets/dpiscine_icon.png';
import img from './assets/img.png';
import nodejs from './assets/nodejs.png';
import tailwind from './assets/tailwind.png';
import proximus from './assets/proximus.png';
import proximusScreen from './assets/proximus_screen.png';
import bootstrap from './assets/bootstrap.png';

const projects = ref([
  {
    id: 1,
    image: gppitIcon,
    title: 'Golden-PPIT',
    summary: 'Projet de synthèse de fin de licence. Création d\'un site web pour une association fictive.',
    description: 'Le projet Golden-PPIT est une plateforme de gestion d\'événements en ligne qui suit une méthodologie agile pour son développement.' +
        ' Le projet est divisé en plusieurs sprints, avec des objectifs spécifiques pour chaque sprint.' +
        ' L\'architecture du projet est basée sur le modèle MVC (Modèle-Vue-Contrôleur).',
    image2: gppit,
    technologies: [
      { name: 'Git', icon: git },
      { name: 'Javascript', icon: js },
      { name: 'PHP', icon: php },
      { name: 'Composer', icon: composer },
      { name: 'MySQL', icon: mysql },
      { name: 'Figma', icon: figma },
      { name: 'Slim', icon: slim }
    ]
  },
  {
    id: 2,
    image: dpiscineIcon,
    title: 'DPiscine',
    summary: 'Projet de Design Pattern, développement d\'une application Web avec une architecture client-serveur pour gérer des agendas.',
    description: 'Ce projet a pour but de mettre en pratique les différents Design Pattern vu en cours. ' +
        'Il fut réalisé en trinôme, nous avons utilisé Tailwind pour le front et Express pour le back.'+
        'Nous avons utilisé la méthode agile Scrum pour la réalisation de ce projet.',
    image2: img,
    technologies: [
      { name: 'Git', icon: git },
      { name: 'Javascript', icon: js },
      { name: 'NodeJS', icon: nodejs },
      { name: 'Tailwind', icon: tailwind }
    ]
  },
  {
    id: 3,
    image: proximus,
    title: 'Talent Advisor',
    summary: 'Développement d\'un module d\'absences dans une application web de gestion de ressources humaines.',
    description: 'Lors de mon stage de fin de licence, j\'ai eu l\'occasion de développer un module d\'absences dans une application web de gestion de ressources humaines.' +
        ' J\'ai pu mettre en pratique mes connaissances en Javascript, PHP et SQL.' +
        ' J\'ai également pu découvrir bootstrap, approfondir mes connaissances en Git ainsi que découvrir le framework FullCalendar.',
    image2: proximusScreen,
    technologies: [
      { name: 'Git', icon: git },
      { name: 'Javascript', icon: js },
      { name: 'PHP', icon: php },
      { name: 'MySQL', icon: mysql },
      { name: 'Bootstrap', icon: bootstrap }
    ]
  },
]);


const selectedProject = ref(null);
const showProjectModal = ref(false);
//const darkMode = ref(false);

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

const showParticles = ref(false);

onMounted(() => {
  setTimeout(() => {
    new Sparticles({
      selector: `.background${showParticles.value ? '.show' : ''}`,
      color: '#2c3e50', // Couleur des particules
      connectParticles: true, // Relier les particules entre elles
      speed: 1, // Vitesse de déplacement des particules
      sizeVariations: 10000, // Variations de taille des particules
      maxParticles: 100, // Nombre maximal de particules
      minDistance: 120, // Distance minimale entre les particules pour la connexion
      responsive: [
        {
          breakpoint: 768,
          options: {
            maxParticles: 80,
            minDistance: 100
          }
        },
        {
          breakpoint: 576,
          options: {
            maxParticles: 50,
            minDistance: 80
          }
        }
      ],
      // Autres options de configuration des particules
    });
    showParticles.value = true;
  }, 200);
});

</script>

