<template>
  <div class="nuggetilla-project-container" v-if="selectedProject">
    <div class="nuggetilla-main">
        <div class="video-wrapper">
          <iframe src="https://www.youtube.com/embed/dCwn-MtEUgU?si=cphB9Qp3nRTL-0IQ&amp;controls=0&amp;autoplay=1" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        </div>
        <span class="text">What began as a pastime during the global pandemic has evolved into a beautiful project dedicated to capturing the memories of special moments,
           cherished friendships, and meaningful places through personalized digital illustrations.</span>
      </div>
      <div class="nuggetilla-slider">
        <div 
          v-for="(pic, index) in images" 
          :key="'nuggetilla_img' + index" 
          class="illustration"
        >
          <img 
            :src="require('@/assets/1.nuggetilla/scroll-images/' + pic)" 
            :alt="'section_project_' + index"
            @click="handleClick(project)"
          >
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
        images: []
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
      }
    }
  }
</script>

<style lang="less">
.nuggetilla-project-container {
    max-height: max-content;
    padding: 0 15vw;
    margin-bottom: 5rem;
    
    .nuggetilla-main {
      gap: 2rem;
      display: flex;
      
      .video-wrapper {
        position: relative;
        padding-bottom: 45%;
        width: 100%;
        height: 90%;
      }
  
      .video-wrapper iframe {
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
        text-align: start;
      }
    }

    .nuggetilla-slider {
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

      .illustration {
        display: flex;
        flex-direction: column;

        img {
          width: 34rem;
          margin-right: 20px;
        }
    }
  }

}
</style>