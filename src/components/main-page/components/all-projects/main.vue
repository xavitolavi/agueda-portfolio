<template>
  <div class="all-projects-container">
    <div class="images-container">
      <div 
        v-for="(project, index) in projects" 
        class="image__item"
        :style="{ 'background-image': 'url(' + require('@/assets/images_lower/' + project.img) + ')' }"
        :key="'project_' + index" @click="$emit('project-select', project)"
      />
    </div>
  </div>
</template>

<script>
export default {

  name: "AllProjects",

  props: {
    projects: {
      type: Array,
      default() {
        return []
      }
    }
  },
}
</script>

<style lang="less">
.all-projects-container {
  padding: 60px;
  max-width: 100%;
  position: relative;

  .images-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    grid-gap: 1rem;
    grid-auto-flow: dense;

    .image__item {
      cursor: pointer;
      width: 100%;
      height: 250px;
      background-size: cover;
      background-position: center;
      transition: .1s ease-in-out;
  
      &:hover {
        transform: scale(1.04)
      }
    }
  }
}
</style>