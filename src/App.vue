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
        <project-item v-for="project in projects" :key="project.id" :project="project" />
      </div>
    </section>

    <section id="contact">
      <h2>Contactez-moi</h2>
      <form>
        <!-- Ajoutez ici les champs de formulaire pour le nom, l'e-mail, le message, etc. -->
        <!-- Ajoutez un bouton de soumission -->
      </form>
    </section>

    <footer>
      <p>&copy; 2023 Mon Portfolio</p>
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
      selectedProject: null
    };
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

</style>
