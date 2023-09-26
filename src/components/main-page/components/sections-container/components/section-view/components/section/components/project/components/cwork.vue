<template>
  <div class="cwork-project-container" v-if="selectedProject">
    <div class="video-wrapper">
      <video autoplay loop>
        <source src="https://res.cloudinary.com/di6ki3nxv/video/upload/v1695309104/cwork.mp4"
          type="video/mp4; codecs=avc1.4d002a">
      </video>
    </div>
    <div class="text">
      <span>
        "Cwork.” is a mobile application that connects people in search of efficient and
        productive coworking spaces with entities and private parties that can offer them.
        In essence, Cwork becomes the perfect companion for those who wish to work remotely
        from their homes.
      </span>
      <div class="video-wrapper mobile">
        <video autoplay loop>
          <source src="https://res.cloudinary.com/di6ki3nxv/video/upload/v1695309104/lower-cwork-scroll.mp4"
            type="video/mp4; codecs=avc1.4d002a">
        </video>
      </div>
      <span>
        <p>This application provides an intuitive and easy-to-use platform where users can search
          and find suitable coworking spaces, with several options available such as cafes,
          coworking spaces, meeting rooms and other spaces equipped with the necessary amenities
          to boost your productivity.</p>

        <br>
        <p>Cwork.'s main features include an advanced filtering system that allows users to search
          for spaces based on location, prices, services offered and ratings from other users.
          In addition, users can book spaces directly through the application and communicate
          directly with hosts, ensuring smooth and convenient communication between interested
          parties.</p>
      </span>
    </div>
    <img class="estora" :src="require('@/assets/7.cwork/estora.jpg')" alt="Estora">
    <div class="images-cwork">
      <div class="left">
        <div class="video-wrapper desktop">
          <video autoplay loop>
            <source src="https://res.cloudinary.com/di6ki3nxv/video/upload/v1695309104/lower-cwork-scroll.mp4"
              type="video/mp4; codecs=avc1.4d002a">
          </video>
        </div>
      </div>
      <div class="right">
        <img class="moodboard" :src="require('@/assets/7.cwork/moodboard.jpg')" alt="Moodboard">
        <img class="ui-kit" :src="require('@/assets/7.cwork/ui-kit.jpg')" alt="UI Kit">
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

  .video-wrapper {
    position: relative;
    padding-bottom: 64.9%;
    height: 0;
  }

  .video-wrapper video {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
  }

  .text {
    margin-top: 2rem;
    text-align: justify;
    display: flex;
    gap: 1.5rem;

    .mobile {
      display: none;
    }

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
    }

    .video-wrapper {
      position: relative;
      padding-bottom: 60%;
      height: 100%;
    }

    .video-wrapper video {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
    }

    .right {
      width: 50%;
    }
  }

  .banner {
    width: 100%;
  }
}

@media (max-width: 768px) {
  .cwork-project-container {

    .text {
      margin-top: 2rem;
      text-align: justify;
      display: flex;
      flex-direction: column;
      gap: 1.5rem;

      .mobile {
        display: block;
        padding-bottom: 100%;
      }

      span {
        width: 100%;
      }
    }

    .estora {
      width: 100%;
    }

    .images-cwork {
      margin-bottom: 1rem;
      
      .left {
        display: none;
      }

      .right {
        width: 100%;

        .moodboard {
          display: none;
        }
      }
    }
  }
}
</style>