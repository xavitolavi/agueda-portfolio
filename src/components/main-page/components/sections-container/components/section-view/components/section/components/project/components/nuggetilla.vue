<template>
  <div class="nuggetilla-project-container" v-if="selectedProject">
      <div class="nuggetilla-main">
        <img :src="require('@/assets/images_lower/' + selectedProject.img)" :alt="selectedProject.img">
        <span>What began as a pastime during the global pandemic has evolved into a beautiful project dedicated to capturing the memories of special moments,
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
    box-sizing: border-box;
    padding-left: 20rem;

    .nuggetilla-main {
      display: flex;
      flex-direction: row;
      gap: 2rem;
      margin-right: 10rem;
      flex-wrap: wrap;
      
      img {
        flex: 50%;
        max-width: 60%;
      }

      span {
        flex: 30%;
        text-align: justify;
        align-self: flex-end;
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
          width: 40rem;
          margin-right: 20px;
        }
    }
  }

}
</style>