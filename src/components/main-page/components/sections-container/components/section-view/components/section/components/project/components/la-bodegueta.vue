<template>
  <div class="bodegueta-project-container" v-if="selectedProject">
    <div class="video-wrapper">
      <video autoplay loop>
        <source src="https://res.cloudinary.com/di6ki3nxv/video/upload/v1695309104/bodegueta.mp4" type="video/mp4; codecs=avc1.4d002a">
      </video>
    </div>
    <div class="bodegueta-text">
      <span>As part of the team responsible for the redesign of La Bodeguera de Rambla Catalunya's website,
        an iconic tavern located in the heart of Barcelona, I have crafted a series of illustrations to capture the
        values,
        personality and essence of this emblematic place. A collection that not only decorates the various sections of the
        site,
        but also enhances the authenticity of this tavern.
      </span>
      <div class="video-wrapper mobile">
        <video autoplay loop>
          <source src="https://res.cloudinary.com/di6ki3nxv/video/upload/v1695309104/bodegueta-carta.mp4" type="video/mp4; codecs=avc1.4d002a">
        </video>
      </div>
      <span>In collaboration with the team, we have worked to offer an attractive visual experience coherent with the
        brand,
        taking care of every aesthetic detail while ensuring an easy and fluid navigation for the visitor. Our goal has
        been to
        make every visit to the website an immersion into the unique atmosphere, culinary delights and history of La
        Bodegueta.
      </span>
    </div>
    <div class="video-wrapper desktop">
      <video autoplay loop>
        <source src="https://res.cloudinary.com/di6ki3nxv/video/upload/v1695309104/bodegueta-carta.mp4" type="video/mp4; codecs=avc1.4d002a">
      </video>
    </div>
    <img :src="require('@/assets/2.bodegueta/frame_captures.jpg')" alt="Frame Captures">
    <div class="small-illustrations">
      <img :src="require('@/assets/2.bodegueta/1.png')" alt="Tapa 1">
      <img :src="require('@/assets/2.bodegueta/2.png')" alt="Tapa 2">
      <img :src="require('@/assets/2.bodegueta/3.png')" alt="Tapa 3">
      <img :src="require('@/assets/2.bodegueta/4.png')" alt="Tapa 4">
    </div>
  </div>
</template>

<script>
export default {
  name: 'LaBodeguetaProject',

  components: {
  },

  props: {
    selectedProject: {
      type: Object,
      default() {
        return {};
      }
    }
  }
}
</script>

<style lang="less">
.bodegueta-project-container {

  img {
    width: 100%;
  }

  .video-wrapper {
    position: relative;
    padding-bottom: 60.9%;
    height: 0;
    margin-bottom: 2rem;
  }

  .mobile {
    display: none;
  }

  .video-wrapper video {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
  }

  .bodegueta-text {
    display: flex;
    flex-direction: row;
    gap: 2rem;
    margin: 2rem 0 2rem 0;

    span {
      text-align: justify;
      width: 50%;
    }

  }

  .small-illustrations {
    margin-top: 3rem;
    display: flex;
    flex-direction: row;
    align-items: center;
    max-width: 100%;
    justify-content: space-between;

    img {
      width: 15%;
      height: 100%;
    }
  }

}

@media (max-width: 768px) {
  .bodegueta-project-container {
    .video-wrapper {
      position: relative;
      padding-bottom: 60.9%;
      width: 100%;
      height: 100%;
      margin-bottom: 0;

      &.mobile {
        display: block;
      }

      &.desktop {
        display: none;
      }
    }

    .video-wrapper .video {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
    }

    .bodegueta-text {
      display: flex;
      flex-direction: column;
      gap: 2rem;
      margin: 2rem 0 2rem 0;

      span {
        text-align: justify;
        width: 100%;
      }

    }

    .small-illustrations {
      margin-top: 2rem;
      display: grid;
      grid-template-columns: auto auto;
      gap: 4rem;
      row-gap: 6rem;

      img {
        width: 95%;
        height: 90%;
      }
    }
  }
}</style>