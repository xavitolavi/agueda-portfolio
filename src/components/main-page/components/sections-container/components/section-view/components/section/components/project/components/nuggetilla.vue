<template>
  <div class="nuggetilla-project-container" v-if="selectedProject">
    <div class="nuggetilla-main">
      <div class="video-wrapper">
        <video autoplay loop>
          <source src="https://res.cloudinary.com/di6ki3nxv/video/upload/v1695309104/nuggetilla-video-hd.mp4"
            type="video/mp4; codecs=avc1.4d002a">
        </video>
      </div>
      <span class="text">What began as a pastime during the global pandemic has evolved into a beautiful project dedicated
        to capturing the memories of special moments,
        cherished friendships, and meaningful places through personalized digital illustrations.</span>
    </div>
    <div class="nuggetilla-slider-container" :class="grabActive" :ref="'slider'" @mousedown="mouseDown">
      <div class="nuggetilla-slider" :style="leftSlider">
        <div v-for="(pic, index) in images" :key="'nuggetilla_img' + index" class="illustration">
          <img :src="require('@/assets/1.nuggetilla/scroll-images/' + pic)" :alt="'nuggetilla_illustration' + index">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NuggetillaProject',

  props: {
    selectedProject: {
      type: Object,
      default() {
        return {};
      }
    }
  },

  data() {
    return {
      images: [],
      left: 0,
      isDown: false,
      startX: null,
      scrollLeft: null,
      projects: [],
      lastPosition: 0,
      sliderWidth: 0
    }
  },

  created() {
    this.setImages();
  },

  methods: {
    setImages() {
      let illustrations = require.context(
        '@/assets/1.nuggetilla/scroll-images',
        true,
        /^.*\.jpg$/
      )

      this.images = illustrations.keys();

      this.images = this.images.map(img => {
        return img.replace('./', '');
      })
    },

    mouseDown(e) {
      e.preventDefault();

      this.start = performance.now();
      this.drag = true;
      this.startX = e.pageX;

      this.lastPosition = e.pageX;

      this._dragCallback = (e) => {
        this.left = this.left - (this.lastPosition - e.pageX)
        this.lastPosition = e.pageX;

        if (this.left <= -1700) {
          this.left = -1699;
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
.nuggetilla-project-container {

  .nuggetilla-main {
    gap: 2rem;
    display: flex;
    padding: 0 17rem;

    .video-wrapper {
      position: relative;
      padding-bottom: 45%;
      width: 100%;
      height: 90%;
    }

    .video-wrapper video {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
    }

    .text {
      flex: 40%;
      display: flex;
      align-self: flex-end;
      text-align: start;
    }
  }

  .nuggetilla-slider-container {
    margin-top: 6rem;
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
    padding-left: 17rem;

    .nuggetilla-slider {
      
      margin-bottom: 1rem;
      display: flex;
      flex-direction: row;
      gap: 12rem;
    }

    .illustration {
      box-shadow: 2px 2px 5px rgba(148, 148, 148, .5);
      display: flex;
      flex-direction: column;
      width: 10rem;
    }
  }

}

@media (max-width: 1440px) {
  .nuggetilla-project-container {
    .nuggetilla-slider-container .nuggetilla-slider .illustration {
      width: 8rem;
    }
  }
}

@media (max-width: 1280px) {
  .nuggetilla-project-container {
    .nuggetilla-main {
      padding: 0 13rem;
    }

    .nuggetilla-slider-container {
      padding-left: 13rem;
    }
  }
}

@media (max-width: 768px) {
  .nuggetilla-project-container {
    .nuggetilla-main {
      gap: 2rem;
      display: flex;
      flex-direction: column;
      padding: 0 30px;

      .video-wrapper {
        position: relative;
        padding-bottom: 65.5%;
        width: 100%;
        height: 100%;
      }

      .video-wrapper video {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
      }

      .text {
        flex: 40%;
        display: flex;
        align-self: flex-end;
        text-align: justify;
      }
    }

    .nuggetilla-slider-container {
      display: block;
      padding: 0;
      
      .nuggetilla-slider {
        justify-items: center;
        display: grid;
        grid-template-columns: auto auto;
        grid-template-rows: auto;
        gap: 3rem;
      }
    }
  }
}
</style>