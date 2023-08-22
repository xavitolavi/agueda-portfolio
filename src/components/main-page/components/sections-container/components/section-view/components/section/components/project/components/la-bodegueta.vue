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
      <img :src="require('@/assets/2.bodegueta/frame_captures.jpg')" alt="Frame Captures">
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
    padding-left: 20rem;
    padding-right: 20rem;

    img {
        width: 100%;
    }

    .bodegueta-text {
      display: flex;
      flex-direction: row;
      gap: 2rem;
      margin: 2rem 0 2rem 0;

      span {
        text-align: justify;
      }

    }

    .small-illustrations {
      display: flex;
      flex-direction: row;
      gap: 3rem;
      align-items: center;
      max-width: 100%;
      
      img {
        width: 100%;
        height: 100%;
      }
    }

}
</style>