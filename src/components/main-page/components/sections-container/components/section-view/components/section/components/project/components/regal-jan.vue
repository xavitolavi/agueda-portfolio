<template>
  <div class="jan-project-container" v-if="selectedProject">
    <div class="images">
      <img class="poster" :src="require('@/assets/images_lower/' + selectedProject.img)" :alt="selectedProject.img">
      <span class="mobile">Nothing but a nice poster I made for my nephew.</span>
      <img class="jan" :src="require('@/assets/6.jan/jan.jpg')" alt="Jan">
    </div>
    <span class="desktop">Nothing but a nice poster I made for my nephew.</span>
  </div>
</template>

<script>
export default {
  name: 'RegalJanProject',

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
.jan-project-container {

  .images {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    gap: 1.5rem;

    .poster {
      width: 70%;
      flex: 60%;
    }

    .mobile {
      display: none;
    }

    .jan {
      width: 25%;
      flex: 25%;
    }
  }

  span {
    margin-top: 1.5rem;
    display: flex;
    align-self: flex-start;
    text-align: justify;
  }
}

@media (max-width: 768px) {
  .jan-project-container {

    .images {
      flex-direction: column;

      .poster {
        width: 100%;
      }

      .mobile {
        display: block;
        margin: 0;
      }

      .jan {
        margin: 0;
        width: 100%;
      }
    }

    span {
      display: none;
    }
  }
}
</style>