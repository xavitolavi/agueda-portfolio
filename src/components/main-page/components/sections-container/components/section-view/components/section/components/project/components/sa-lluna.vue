<template>
  <div class="sa-lluna-container" v-if="selectedProject">
    <div class="images desktop">
      <img class="camisetes" :src="require('@/assets/10.sa-lluna/1.jpg')" alt="Camisetes">
      <img class="lluna" :src="require('@/assets/10.sa-lluna/2.jpg')" alt="Sa Lluna logo">
    </div>
    <img class="cartes" :src="require('@/assets/10.sa-lluna/3.jpg')" alt="Cartes">
    <span>
      Sa LLuna is a must-visit destination for those looking to sample authentic Mediterranean cuisine during their 
      visit to Cala Galdana. With more than three decades of history in Menorca, and as part of its renovation process,
       we have embarked on a rebranding project to enrich the essence and evolution of this iconic restaurant.<br>

      <br>Taking inspiration from the old mural that has adorned one of the restaurant's walls for years, my goal was 
      to create a new uniform that not only honored its past, but also projected a fresh and contemporary image in 
      perfect alignment with Sa LLuna's vision for the future.<br>

      <br>I also had the privilege of contributing to the creation of new promotional materials. A crucial 
      element was the conception of a business card. For this, I rescued the old and emblematic logo, 
      breathing new life into it through a minimalist, clear, and elegant composition, all colored in a 
      blue palette to capture its Mediterranean character.
    </span>
    <div class="images mobile">
      <img class="lluna" :src="require('@/assets/10.sa-lluna/2.jpg')" alt="Sa Lluna logo">
      <img class="camisetes" :src="require('@/assets/10.sa-lluna/1.jpg')" alt="Camisetes">
    </div>
  </div>
</template>

<script>
  export default {
    name: 'SaLlunaProject',

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
.sa-lluna-container {

    .images {
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: space-between;
      gap: 1rem;

      .camisetes {
        width: 60%;
        flex: 55%;
      }

      .lluna {
        width: 30%;
        flex: 30%;
      }

      &.mobile {
        display: none;
      }
    }

    .cartes {
      margin-top: 2rem;
      width: 100%;
    }

    span {
      margin-top: 1.5rem;
      display: flex;
      align-self: flex-start;
      text-align: justify;
    }
}

@media (max-width: 768px) {
  .sa-lluna-container {

    .images {
      margin-top: 2rem;
      &.mobile {
        display: flex;
        flex-direction: column;

        .lluna {
          align-self: center;
          width: 70%;
        }

        .camisetes {
          margin-top: 1rem;
          width: 100%;
        }
      }

      &.desktop {
        display: none;
      }
    }
  }
}
</style>