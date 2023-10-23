<template>
  <div class="champagne-project-container" v-if="selectedProject">
    <div class="content">
      <span class="mobile-champagne">Design and illustration of the cover of the book "Champagne en vasos de plástico", an exciting youth road trip
        that narrates the adventures of a group of teens as they explore the most authentic and deepest Spain.
      </span>
      <div class="media">
        <img :src="require('@/assets/5.champagne/champagne_img.jpg')" alt="Champagne">
        <div class="right">
          <div class="video-wrapper">
            <video :autoplay="!isMobile" loop muted :controls="isMobile">
              <source src="https://res.cloudinary.com/di6ki3nxv/video/upload/v1695490638/champagne_2_rtms51.mp4"
                type="video/mp4; codecs=avc1.4d002a">
            </video>
          </div>
        </div>
      </div>
      <span class="desktop-champagne">Design and illustration of the cover of the book "Champagne en vasos de plástico", an exciting youth road trip
        that narrates the adventures of a group of teens as they explore the most authentic and deepest Spain.
      </span>
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
    },

    isMobile: {
      type: Boolean,
      default: false
    }
  },
}
</script>

<style lang="less">
.champagne-project-container {
  .content {
    display: flex;
    flex-direction: row;
    gap: 1.5rem;
    flex-wrap: wrap;

    .mobile-champagne {
      display: none;
    }

    .media {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      flex: 65%;

      img {
        width: 48%;
      }

      .right {
        position: relative;
        width: 48%;
      }

      .video-wrapper {
        display: block;
        position: relative;
        height: 100%;
      }

      .video-wrapper video {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
      }
    }

    span {
      width: 30%;
      flex: 25%;
      align-self: flex-end;
      text-align: justify;
    }

  }
}

@media (max-width: 1024px) {
  .champagne-project-container {
    .content {
      span {
        margin-top: 2rem;
        width: 100%;
        flex: 100%;
      }
    }
  }
}

@media (max-width: 768px) {
  .champagne-project-container {
    .content {
      flex-direction: column;

      .mobile-champagne {
        display: block;
        margin-bottom: 1rem;
      }

      .media {
        flex-direction: column;
        width: 100%;

        img {
          display: none;
        }

        .right{
          position: relative;
          width: 100%;

          .video-wrapper {
            padding-bottom: 0;

            video {
              position: relative;
            }
          }
        }
      }

      span {
        margin-top: 2rem;
        width: 100%;
      }

      .desktop-champagne {
        display: none;
      }
    }
  }
}
</style>