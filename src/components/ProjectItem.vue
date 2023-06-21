<template>
  <div class="project-item" @click="openProjectModal">
    <img :src="project.image" alt="Image du projet">
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
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 25vw;
  height: calc(25vw * 1.4);
  background: linear-gradient(135deg, #f9f9f9, #e4e4e4);
  border-radius: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  position: relative;
  overflow: hidden;
  transform: rotate(0deg);
  transition: transform 0.3s ease;
}

.project-item:before {
  content: "";
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle at center, rgba(176,196,222, 0.1) 0%, transparent 70%);
  opacity: 0;
  transition: opacity 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  z-index: 1;
}

.project-item:hover:before {
  opacity: 1;
}

.project-item:hover {
  transform: rotate(5deg) scale(1.05);
  box-shadow: 0 0 0 10px rgba(176,196,222, 0.1);
}

.project-item h3 {
  margin-top: 10px;
  font-size: 18px;
  color: #2c3e50;
  text-align: center;
  transition: color 0.3s ease;
  z-index: 2;
}

.project-item:hover h3 {
  color: #333333;
}

.project-item p {
  margin: 10px;
  font-size: 14px;
  color: #333333;
  text-align: center;
  transition: color 0.3s ease;
  z-index: 2;
}

.project-item p::after {
  content: "";
  display: block;
  width: 50%;
  height: 1px;
  margin: 10px auto;
  background-color: #2c3e50;
}

.project-item:hover p {
  color: #333333;
}

.project-item:hover p::after {
  background-color: #333333;
}

.project-item:focus {
  outline: none;
}

@keyframes border-animation {
  0% {
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
    transform: rotate(0deg);
  }
  50% {
    box-shadow: 0 0 0 10px rgba(44, 62, 80, 0.1);
    transform: rotate(5deg);
  }
  100% {
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
    transform: rotate(0deg);
  }
}

.project-item:hover {
  animation: border-animation 2s infinite;
}
</style>









