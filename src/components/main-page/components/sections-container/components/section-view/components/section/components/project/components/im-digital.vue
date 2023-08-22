<template>
  <div class="digital-project-container" v-if="selectedProject">
      <img :src="require('@/assets/images_lower/' + selectedProject.img)" :alt="selectedProject.img">
  </div>
</template>

<script>
  export default {
    name: 'ImDigitalProject',

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
.digital-project-container {
    max-height: max-content;
    padding-left: 20rem;

    img {
        width: 60rem;
    }

}
</style>