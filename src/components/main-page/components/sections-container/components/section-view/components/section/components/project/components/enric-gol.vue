<template>
  <div class="enric-project-container" v-if="selectedProject">
      <div class="video-wrapper">
        <iframe src="https://www.youtube.com/embed/RxiH__-602o?si=B6MmZlRmupiijD-m&amp;controls=1&amp;autoplay=1" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
      </div>
      <div class="main-text">
        <span><p>This project has been a fulfilling journey, allowing me to leverage and integrate a 
          diverse range of skills and knowledge acquired throughout my studies and professional 
          experience. The main objective of the project was to create an attractive website to 
          showcase the exceptional talent of this Menorcan artist, while expanding the reach of 
          his market beyond the local level.</p><br>

          <p>As a result, the website has become the primary destination for those seeking to connect 
          or acquire pieces from this multifuncional artist. The site boasts a clean and intuitive 
          design that exudes elegance and subtlety, perfectly complementing the exceptionally high 
          quality of the exhibited works. Besides the web design, I have also assumed the 
          responsibility of creating all the written content and directing the photography, as 
          well as developing the visual and corporate identity of the artist.</p> </span>
      </div>
      <div class="enric-slider">

      </div>
      <div class="secondary-text">
        Even though, my commitment to the project extends beyond the website design, as I have also 
        managed and created content for the social networks in order to promote the artist's work and 
        connect him with his target audience.
      </div>
      <div class="portraits">
        <img :src="require('@/assets/8.enric-gol/1.png')" alt="Fig 1">
        <img :src="require('@/assets/8.enric-gol/2.png')" alt="Fig 2">
        <img :src="require('@/assets/8.enric-gol/3.png')" alt="Fig 3">
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
      }
    },
  }
</script>

<style lang="less">
.enric-project-container {
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

    .main-text {
      margin: 2rem 0;
      text-align: justify;
    }

    .secondary-text {
      margin: 2rem 0;
      text-align: justify;
      width: 50%;
    }

    .portraits {
      display: flex;
      flex-direction: row;
      justify-content: space-between;

      img {
        width: 32.2%;
      }
    }
}
</style>