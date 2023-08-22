<template>
  <div class="volver-project-container" v-if="selectedProject">
    <div class="media">
      <img :src="require('@/assets/images_lower/' + selectedProject.img)" alt="Volver a ser yo video" class="video">
      <img :src="require('@/assets/3.volver/portada.jpg')" alt="Volver a ser yo image" class="image">
    </div>
    <div class="volver-text">
      <span>
        <p>Editorial design, layout and illustration of "Volver a ser yo", a practical guide to help heal the heart after a breakup. 
        In this project, I have been in charge of giving life to the main character  and making sure to capture the healing process in a genuine way.</p>
  
        <br><p>The result has been a collection of thirty illustrations, one for each chapter of the book, that accompany and enrich the narrative, 
        providing a strong visual connection between the reader and the content. Additionally, I have been responsible for the book's layout, 
        carefully considering the choice of typography, structure, and final finishes to achieve a presentation that is harmonious and coherent with 
        the theme and target audience it is intended for.</p>
      </span>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'VolverASerYoProject',

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
.volver-project-container {
    box-sizing: border-box;
    padding-left: 20rem;
    max-width: 100%;
    padding-right: 20rem;

    .media {
      display: flex;
      flex-direction: row;
      gap: 1.5rem;
      flex-wrap: wrap;

      .video {
        width: 60%;
        flex: 60%;
      }

      .image {
        width: 20%;
        flex: 30%;
      }
    }

    .volver-text {
      margin: 2rem 0 3rem 0;
      span {
        text-align: justify;
      }
    }

}
</style>