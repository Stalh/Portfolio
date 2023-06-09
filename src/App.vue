<template>
  <div id="app">
    <header>
      <h1>Mon Portfolio</h1>
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
        <h2>Bienvenue sur mon portfolio</h2>
        <p>Découvrez mes projets et compétences</p>
        <a href="#projects" class="cta-button">Voir mes projets</a>
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
      <h2>Mes projets</h2>
      <div class="project-grid">
        <project-item v-for="project in projects" :key="project.id" :project="project" @open-project-modal="openProjectModal" />
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
      <h2>Contactez-moi</h2>
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
      <p>&copy; Guillaume Zimol 2023</p>
    </footer>
  </div>
</template>

<script>
import ProjectItem from './components/ProjectItem.vue';

export default {
  name: 'App',
  components: {
    ProjectItem
  },
  data() {
    return {
      projects: [
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
        // Ajoutez d'autres projets ici
      ],
      selectedProject: null,
      showProjectModal: false
    };
  },
  methods: {
    openProjectModal(project) {
      this.selectedProject = project;
      this.showProjectModal = true;
    },
    closeProjectModal() {
      this.selectedProject = null;
      this.showProjectModal = false;
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

header {
  padding: 20px;
  background-color: #f2f2f2;
}

nav ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

nav ul li {
  display: inline-block;
  margin-right: 10px;
}

nav ul li a {
  text-decoration: none;
  color: #2c3e50;
}

#hero {
  background-size: cover;
  background-position: center;
  color: #2c3e50;
  padding: 100px 0;
}

.hero-content {
  max-width: 600px;
  margin: 0 auto;
}

#about {
  padding: 50px 0;
  background-color: #f2f2f2;
}

#projects {
  padding: 50px 0;
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

#contact {
  padding: 50px 0;
  background-color: #f2f2f2;
}

footer {
  padding: 20px;
  background-color: #f2f2f2;
}

.about-info {
  display: flex;
  align-items: center;
}

.profile-image {
  width: 350px; /* Ajustez la taille selon vos besoins */
  height: auto;
  margin-right: 20px; /* Espace entre l'image et le texte */
  margin-left: 75px; /* Décalage horizontal */
}

.social-icon-container {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.social-icon {
  width: 30px;
  height: 30px;
  transition: transform 0.3s ease;
}

.social-icon:hover {
  transform: scale(1.2);
}

.contact-links {
  display: flex;
  justify-content: center;
  align-items: center;
  padding-left: 20px;
}

.project-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  backdrop-filter: blur(8px); /* Ajoute le flou */
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  border: 1px solid #2c3e50; /* Ajoute une bordure solide */
  max-width: 800px; /* Modifie la largeur de la modal */
}

.modal-content h3 {
  font-size: 20px;
  margin-bottom: 10px;
}

.modal-content p {
  margin-bottom: 20px;
}

.modal-content button {
  background-color: #2c3e50;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}

.modal-content button:hover {
  background-color: #34495e;
}


</style>
