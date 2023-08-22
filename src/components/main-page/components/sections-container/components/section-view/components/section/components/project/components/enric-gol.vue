<template>
  <div class="enric-project-container" v-if="selectedProject">
      <img :src="require('@/assets/images_lower/' + selectedProject.img)" :alt="selectedProject.img">
  </div>
</template>

<script>
  export default {
    name: 'EnricGolProject',

    props: {
      selectedProject: {
          type: Object,
          default() {
              return {};
          }
      }
    },
  }
</script>

<style lang="less">
.enric-project-container {
    max-height: max-content;
    padding-left: 20rem;

    img {
        width: 60rem;
    }

}
</style>