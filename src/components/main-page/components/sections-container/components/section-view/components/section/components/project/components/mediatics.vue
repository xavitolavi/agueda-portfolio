<template>
  <div class="mediatics-project-container" v-if="selectedProject">
    <div class="video-wrapper">
      <iframe src="https://player.vimeo.com/video/858147977?h=d6143b0110&autoplay=1&title=0&byline=0&portrait=0" style="position:absolute;top:0;left:0;width:100%;height:100%;" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen />
    </div>
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
      }
    },
  }
</script>

<style lang="less">
.main-container {
  margin-top: 140px;
}

.mediatics-project-container {
    max-height: max-content;
    padding: 0 20rem;
    margin-bottom: 5rem;

    .video-wrapper {
      position: relative;
      padding-bottom: 56.25%;
      height: 0;
    }

    .video-wrapper iframe {
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