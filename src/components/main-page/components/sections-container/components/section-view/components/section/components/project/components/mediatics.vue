<template>
  <div class="mediatics-project-container" v-if="selectedProject" :class="{'is-video' : isVideo}">
    <div class="video-wrapper">
      <video controls :autoplay="!isMobile">
        <source src="https://res.cloudinary.com/di6ki3nxv/video/upload/v1695309104/MEDIATICS.mp4" type="video/mp4; codecs=avc1.4d002a">
      </video>    </div>
    <div class="text">
      <span>Alongside the rest of the creative team at Mediatics, a digital agency specializing in 
      web design, we took on the exciting challenge of rebranding the company. Therefore, I have 
      worked to develop a captivating corporate video to showcase our latest projects with a more 
      refreshing and vibrant perspective, perfectly in line with the company's new vision.</span>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'MediaticsProject',

    props: {
      selectedProject: {
          type: Object,
          default() {
              return {};
          }
      },

      isVideo: {
        type: Boolean,
        default: false
      },

      isMobile: {
        type: Boolean,
        default: false
      }
    },
  }
</script>

<style lang="less">
.main-container {
  margin-top: 140px;
}

.mediatics-project-container {

  &.is-video {
    color: white;
  }
  
    .video-wrapper {
      position: relative;
      padding-bottom: 56.25%;
      height: 0;
    }

    .video-wrapper video {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
    }

    .text {
      margin-top: 2rem;
      text-align: justify;
    }
}
</style>