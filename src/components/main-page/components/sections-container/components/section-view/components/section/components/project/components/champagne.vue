<template>
  <div class="champagne-project-container" v-if="selectedProject">
    <div class="media">
      <img :src="require('@/assets/5.champagne/mock-up.jpg')" alt="Champagne">
      <span>Design and illustration of the cover of the book "Champagne en vasos de plástico", an exciting youth road trip that narrates the adventures of a group of teens as they explore the most authentic and deepest Spain.</span>
    </div>  
  </div>
</template>

<script>
  export default {
    name: 'ChampagneProject',

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
.champagne-project-container {
    max-height: max-content;
    padding-left: 20rem;
    padding-right: 20rem;
    margin-bottom: 5rem;

    .media {
      display: flex;
      flex-direction: row;
      gap: 1.5rem;
      flex-wrap: wrap;

      img {
        width: 60%;
        flex: 70%;
      }

      span {
        width: 30%;
        flex: 20%;
        align-self: flex-end;
        text-align: justify;
      }

    }

}
</style>