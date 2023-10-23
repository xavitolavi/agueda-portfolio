<template>
  <div class="enric-project-container" v-if="selectedProject">
    <div class="enric-top-container">
      <div class="video-wrapper">
        <video :autoplay="!isMobile" loop :controls="isMobile">
          <source src="https://res.cloudinary.com/di6ki3nxv/video/upload/v1695309104/enric-gol.mp4"
            type="video/mp4; codecs=avc1.4d002a">
        </video>
      </div>
      <div class="main-text">
        <span>
          <p>This project has been a fulfilling journey, allowing me to leverage and integrate a
            diverse range of skills and knowledge acquired throughout my studies and professional
            experience. The main objective of the project was to create an attractive website to
            showcase the exceptional talent of this Menorcan artist, while expanding the reach of
            his market beyond the local level.</p><br>

          <p>As a result, the website has become the primary destination for those seeking to connect
            or acquire pieces from this multifuncional artist. The site boasts a clean and intuitive
            design that exudes elegance and subtlety, perfectly complementing the exceptionally high
            quality of the exhibited works. Besides the web design, I have also assumed the
            responsibility of creating all the written content and directing the photography, as
            well as developing the visual and corporate identity of the artist.</p>
        </span>
      </div>
    </div>
    
    <div class="enric-slider-container" :class="grabActive" :ref="'slider'" @mousedown="mouseDown">
      <div class="enric-slider" :style="leftSlider">
        <div class="illustration">
          <img :src="require('@/assets/8.enric-gol/scroll/1.png')" alt="Fig 1">
        </div>
        <div class="illustration">
          <img :src="require('@/assets/8.enric-gol/scroll/2.png')" alt="Fig 1">
        </div>
        <div class="illustration">
          <img :src="require('@/assets/8.enric-gol/scroll/3.png')" alt="Fig 1">
        </div>
        <div class="illustration">
          <img :src="require('@/assets/8.enric-gol/scroll/4.png')" alt="Fig 1">
        </div>
        <div class="illustration">
          <img :src="require('@/assets/8.enric-gol/scroll/5.png')" alt="Fig 1">
        </div>
        <div class="illustration">
          <img :src="require('@/assets/8.enric-gol/scroll/6.png')" alt="Fig 1">
        </div>
      </div>
    </div>

    <div class="enric-bottom-container">
      <div class="secondary-text desktop">
        Even though, my commitment to the project extends beyond the website design, as I have also
        managed and created content for the social networks in order to promote the artist's work and
        connect him with his target audience.
      </div>
      <div class="as-a-result">
        As a result, the website has become the primary destination for those seeking to connect
        or acquire pieces from this multifuncional artist. The site boasts a clean and intuitive
        design that exudes elegance and subtlety, perfectly complementing the exceptionally high
        quality of the exhibited works. Besides the web design, I have also assumed the
        responsibility of creating all the written content and directing the photography, as
        well as developing the visual and corporate identity of the artist.
      </div>
      <div class="portraits">
        <div class="portrait">
          <img :src="require('@/assets/8.enric-gol/1.png')" alt="Fig 1">
        </div>
        <div class="portrait">
          <img :src="require('@/assets/8.enric-gol/2.png')" alt="Fig 2">
        </div>
        <div class="portrait">
          <img :src="require('@/assets/8.enric-gol/3.png')" alt="Fig 3">
        </div>
        <div class="portrait">
          <div class="secondary-text mobile">
            Even though, my commitment to the project extends beyond the website design, as I have also
            managed and created content for the social networks in order to promote the artist's work and
            connect him with his target audience.
          </div>
        </div>
      </div>
    </div>
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
    },

    isMobile: {
      type: Boolean,
      default: false
    }
  },

  data() {
    return {
      left: 0,
      isDown: false,
      startX: null,
      scrollLeft: null,
      projects: [],
      lastPosition: 0,
      sliderWidth: 0
    }
  },

  methods: {
    mouseDown(e) {
      e.preventDefault();

      this.start = performance.now();
      this.drag = true;
      this.startX = e.pageX;

      this.lastPosition = e.pageX;

      this._dragCallback = (e) => {
        this.left = this.left - (this.lastPosition - e.pageX)
        this.lastPosition = e.pageX;

        if (this.left <= -1800) {
          this.left = -1799;
        }

        if (this.left >= 0) {
          this.left = -1;
        }
      }

      this._mouseUpCallback = () => {
        window.removeEventListener("mousemove", this._dragCallback);
        window.removeEventListener("mouseup", this._mouseUpCallback);
      }

      window.addEventListener("mousemove", this._dragCallback);
      window.addEventListener("mouseup", this._mouseUpCallback);
    },
  },


  computed: {
    grabActive() {
      if (this.isDown) {
        return "active";
      }

      return "";
    },

    leftSlider() {
      return `margin-left : ${this.left}px`;
    }
  }
}
</script>

<style lang="less">
.enric-project-container {

  .enric-top-container {
    padding: 0 22rem;

    .video-wrapper {
      position: relative;
      padding-bottom: 64.8%;
      height: 0;
    }

    .video-wrapper video {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
    }

    .main-text {
      margin: 2rem 0;
      text-align: justify;
    }
  }
  

  .enric-slider-container {
    display: flex;
    flex-direction: row;
    position: relative;
    overflow-x: hidden;
    overflow-y: hidden;
    white-space: nowrap;
    transition: all 0.2s;
    will-change: transform;
    user-select: none;
    cursor: pointer;
    padding-left: 22rem;

    .enric-slider {
      display: flex;
      flex-direction: row;
    }

    .illustration {
      display: flex;
      flex-direction: column;

      img {
        width: 25rem;
        margin-right: 20px;
      }
    }
  }

  .enric-bottom-container {
    padding: 0 22rem;

    .secondary-text {
      margin: 2rem 0;
      text-align: justify;
      width: 50%;

      &.mobile {
        display: none;
      }
    }

    .as-a-result {
      display: none;
    }

    .portraits {
      display: flex;
      gap: 1rem;
      flex-direction: row;
      justify-content: space-between;
      
      .portrait {
        width: 100%;

        img {
          height: 100%;
          width: 100%;
        }

        &:last-child {
          display: none;
        }
      }
    }
  }
}

@media (min-width: 1500px) {
  .enric-project-container {

    .enric-top-container {
      padding: 0 30rem;

    }

    .enric-slider-container {
      padding-left: 30rem;
    }

    .enric-bottom-container {
      padding: 0 30rem;
    }
  }
}

@media (max-width: 1280px) {
  .enric-project-container {
    .enric-top-container {
      padding: 0 13rem;
    }

    .enric-slider-container {
      padding-left: 13rem;

      .illustration {
        img {
          width: 15rem;
        }
      }
    }

    .enric-bottom-container {
      padding: 0 13rem;
    }
  }
}

@media (max-width: 768px) {
  .enric-project-container {

    .enric-top-container {
      padding: 0 30px;
    }

    .enric-slider-container {
      display: block;
      padding: 0;

      .enric-slider {
        justify-items: center;
        display: grid;
        grid-template-columns: auto auto;
        grid-template-rows: auto;

        .illustration {
          display: flex;
          flex-direction: column;

          img {
            width: 100%;
          }
        }
      }
    }

    .enric-bottom-container {
      padding: 0 30px;
      
      .secondary-text {

        &.desktop {
          display: none;
        }

        &.mobile {
          width: 100%;
          display: block;
          margin: 0;
        }
      }

      .as-a-result {
        margin: 1rem 0 2rem 0;
        text-align: justify;
        display: block;
      }

      .portraits {
        justify-items: center;
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 1rem;

        .portrait {
          width: 100%;
          text-align: -webkit-center;
          
          &:last-child {
            display: block;
          }
        }

        img {
          width: 100%;
        }

      }
    }    
  }
}
</style>