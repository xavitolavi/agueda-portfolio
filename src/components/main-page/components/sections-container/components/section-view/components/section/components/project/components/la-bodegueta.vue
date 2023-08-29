<template>
  <div class="bodegueta-project-container" v-if="selectedProject">
      <img :src="require('@/assets/images_lower/' + selectedProject.img)" :alt="selectedProject.img">
      <div class="bodegueta-text">
        <span>As part of the team responsible for the redesign of La Bodeguera de Rambla Catalunya's website, 
          an iconic tavern located in the heart of Barcelona, I have crafted a series of illustrations to capture the values, 
          personality and essence of this emblematic place. A collection that not only decorates the various sections of the site, 
          but also enhances the authenticity of this tavern.
        </span>
        <span>In collaboration with the team, we have worked to offer an attractive visual experience coherent with the brand, 
          taking care of every aesthetic detail while ensuring an easy and fluid navigation for the visitor. Our goal has been to 
          make every visit to the website an immersion into the unique atmosphere, culinary delights and history of La Bodegueta.
        </span>
      </div>
      <div class="video-wrapper">
        <iframe src="https://www.youtube.com/embed/-9W9v5gr24c?si=qKVLrEm56F002OiD&amp;controls=0&amp;autoplay=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
      </div>
      <div class="video-wrapper">
        <iframe src="https://www.youtube.com/embed/Ml0NHehC8CE?si=nD-EBE4FyxgVVnRi&amp;controls=0&amp;autoplay=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
      </div>
      <img :src="require('@/assets/2.bodegueta/frame_captures.jpg')" alt="Frame Captures">
      <div class="small-illustrations">
        <img :src="require('@/assets/2.bodegueta/1.png')" alt="Frame Captures">
        <img :src="require('@/assets/2.bodegueta/2.png')" alt="Frame Captures">
        <img :src="require('@/assets/2.bodegueta/3.png')" alt="Frame Captures">
        <img :src="require('@/assets/2.bodegueta/4.png')" alt="Frame Captures">
      </div>
  </div>
</template>

<script>
  export default {
    name: 'LaBodeguetaProject',

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
.bodegueta-project-container {
    max-height: max-content;
    padding: 0 20rem;
    margin-bottom: 5rem;

    img {
        width: 100%;
    }

    .video-wrapper {
      position: relative;
      padding-bottom: 56.25%;
      height: 0;
      margin-bottom: 2rem;
    }

    .video-wrapper iframe {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
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
      margin-top: 1rem;
      display: flex;
      flex-direction: row;
      align-items: center;
      max-width: 100%;
      
      img {
        width: 25%;
        height: 100%;
      }
    }

}
</style>