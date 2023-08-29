<template>
  <div class="cwork-project-container" v-if="selectedProject">
    <div class="video-wrapper">
      <iframe src="https://www.youtube.com/embed/Pvkd8O9GGY8?si=yUK7fyNpUD6OTsi8&amp;controls=1&amp;autoplay=1" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
    </div>      
    <div class="text">
      <span>
        "Cwork.” is a mobile application that connects people in search of efficient and 
        productive coworking spaces with entities and private parties that can offer them. 
        In essence, Cwork becomes the perfect companion for those who wish to work remotely 
        from their homes.
      </span>
      <span>
        <p>This application provides an intuitive and easy-to-use platform where users can search 
        and find suitable coworking spaces, with several options available such as cafes, 
        coworking spaces, meeting rooms and other spaces equipped with the necessary amenities 
        to boost your productivity.</p>

        <br><p>Cwork.'s main features include an advanced filtering system that allows users to search 
        for spaces based on location, prices, services offered and ratings from other users. 
        In addition, users can book spaces directly through the application and communicate 
        directly with hosts, ensuring smooth and convenient communication between interested 
        parties.</p>
      </span>
    </div>
    <img class="estora" :src="require('@/assets/7.cwork/estora.jpg')" alt="Estora">
    <div class="images-cwork">
      <div class="left">
        <iframe src="https://www.youtube.com/embed/MbOllGDXQyo?si=PLZ0EZ55JufwvlDV&amp;controls=1&amp;autoplay=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
      </div>
      <div class="right">
        <img :src="require('@/assets/7.cwork/moodboard.jpg')" alt="Moodboard">
        <img :src="require('@/assets/7.cwork/ui-kit.jpg')" alt="UI Kit">
      </div>
    </div>
    <img class="banner" :src="require('@/assets/7.cwork/poster.jpg')" alt="Banner">
  </div>
</template>

<script>
  export default {
    name: 'CworkProject',

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
.cwork-project-container {
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
      display: flex;
      gap: 1.5rem;

      span {
        width: 50%;
      }
    }

    .estora {
      width: 50%;
    }

    .images-cwork {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      gap: 1.5rem;
      margin-bottom: 2rem;

      img {
        width: 100%;
      }

      .left {
        margin-top: 1rem;
        position: relative;
        padding-bottom: 56.25%;
        width: 50%;
      }

      .left iframe {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 97%;
      }

      .right {
        width: 50%;
      }
    }

    .banner {
      width: 100%;
    }

}
</style>