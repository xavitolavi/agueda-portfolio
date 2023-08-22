<template>
  <div class="gaudeix-project-container" v-if="selectedProject">
      <img :src="require('@/assets/images_lower/' + selectedProject.img)" :alt="selectedProject.img">
      <div class="gaudeix-text">
        <span>I had the pleasure of participating in the "Gaudeix la festa" initiative, promoted by the youth association Oliana Jove, aimed at creating a cultural and social program for the younger generations in this community. My role involved designing and conceptualizing the visual elements that accompany this campaign, paying close attention to both aesthetics and functionality.
        </span>
      </div>
      <div class="gaudeix-fotos-1">
        <img :src="require('@/assets/4.gaudeix/gots.jpg')" alt="Gots">
        <img :src="require('@/assets/4.gaudeix/poster.jpg')" alt="Poster">
      </div>
      <div class="gaudeix-fotos-2">
        <img :src="require('@/assets/4.gaudeix/samarreta.jpg')" alt="Samarreta">
      </div>
  </div>
</template>

<script>
  export default {
    name: 'GaudeixLaFestaProject',

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
.gaudeix-project-container {
    box-sizing: border-box;
    padding-left: 20rem;
    padding-right: 20rem;
    margin-bottom: 5rem;
    img {
        width: 100%;
        height: 70%;
    }

    .gaudeix-text {
      display: flex;
      margin: 2rem 0 2rem 0;
      width: 50%;

      span {
        text-align: justify;
      }

    }

    .gaudeix-fotos-1 {
      display: flex;
      flex-direction: row;
      gap: 1.5rem;

      img {
        width: 50%;
        flex: 50%;
      }
    }

    .gaudeix-fotos-2 {
      display: flex;
      flex-direction: row-reverse;
      gap: 1.5rem;

      img {
        margin-left: 1.5rem;
        width: 50%;
      }
    }

}
</style>