<template>
  <div class="jan-project-container" v-if="selectedProject">
    <div class="images">
      <img class="poster" :src="require('@/assets/images_lower/' + selectedProject.img)" :alt="selectedProject.img">
      <img class="jan" :src="require('@/assets/6.jan/jan.jpg')" alt="Jan">
    </div>
    <span>Nothing but a nice poster I made for my nephew.</span>
  </div>
</template>

<script>
  export default {
    name: 'RegalJanProject',

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
.jan-project-container {
    max-height: max-content;
    padding: 0 20rem 0 20rem;
    margin-bottom: 5rem;

    .images {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        gap: 1.5rem;

        .poster {
          width: 70%;
          flex: 60%;
        }

        .jan {
          width: 25%;
          flex: 25%;
        }
    }

    span {
      margin-top: 1.5rem;
      display: flex;
      align-self: flex-start;
      text-align: justify;
    }
}
</style>