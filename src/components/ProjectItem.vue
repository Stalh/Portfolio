<template>
  <div class="project-item" @click="openProjectModal">
    <img :src="project.image" alt="Image du projet" class="project-image">
    <h3>{{ project.title }}</h3>
    <p>{{ project.summary }}</p>
    <!-- <slot/> -->
  </div>
</template>

<script>
export default {
  name: 'ProjectItem',
  props: ['project'],
  methods: {
    openProjectModal() {
      this.$emit('open-project-modal', this.project);
    }
  }
};
</script>

<style scoped>
.project-item {
  cursor: pointer;
  margin-bottom: 20px;
}

.project-image {
  border-radius: 10px;
}
</style>
