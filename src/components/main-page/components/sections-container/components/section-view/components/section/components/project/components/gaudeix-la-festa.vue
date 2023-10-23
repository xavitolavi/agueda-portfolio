<template>
  <div class="gaudeix-project-container" v-if="selectedProject">
    <div class="video-wrapper">
      <video :autoplay="!isMobile" loop :controls="isMobile">
        <source src="https://res.cloudinary.com/di6ki3nxv/video/upload/v1695309104/gaudeix-la-festa.mp4"
          type="video/mp4; codecs=avc1.4d002a">
      </video>
    </div>
    <div class="gaudeix-text">
      <span>I had the pleasure of participating in the "Gaudeix la festa" initiative, promoted by the youth association
        Oliana Jove, aimed at creating a cultural and social program for the younger generations in this community. My
        role involved designing and conceptualizing the visual elements that accompany this campaign, paying close
        attention to both aesthetics and functionality.
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
    },

    isMobile: {
      type: Boolean,
      default: false
    }
  },
}
</script>

<style lang="less">
.gaudeix-project-container {

  .video-wrapper {
    position: relative;
    padding-bottom: 56.95%;
    height: 0;
  }

  .video-wrapper video {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
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
    justify-content: space-between;

    img {
      width: 49%;
    }
  }

  .gaudeix-fotos-2 {
    margin-top: 2rem;
    display: flex;
    flex-direction: row-reverse;

    img {
      margin-left: 1.5rem;
      width: 49%;
    }
  }
}

@media (max-width: 768px) {
  .gaudeix-project-container {
    .gaudeix-text {
      width: 100%;
    }

    .gaudeix-fotos-1 {
      flex-direction: column;
      align-items: center;

      img {
        margin-bottom: 2rem;
        width: 100%;
      }
    }

    .gaudeix-fotos-2 {
      margin: 0;
      flex-direction: column;
      align-items: center;

      img {
        width: 100%;
        margin: 0;
      }
    }
  }
}
</style>