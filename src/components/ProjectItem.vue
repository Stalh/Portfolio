<template>
  <div class="project-item" @click="showDetails = !showDetails">
    <img :src="project.image" alt="Image du projet" class="project-image">
    <h3>{{ project.title }}</h3>
    <p>{{ project.summary }}</p>
    <div v-if="showDetails">
      <p>{{ project.description }}</p>
      <!-- Ajoutez ici d'autres détails spécifiques au projet -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProjectItem',
  props: ['project'],
  data() {
    return {
      showDetails: false
    };
  }
};
</script>

<style scoped>
.project-item {
  cursor: pointer;
  margin-bottom: 20px;
}

.project-image {
  border-radius: 10px; /* Ajoutez des bords arrondis */
}
</style>
