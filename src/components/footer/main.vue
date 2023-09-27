<template>
  <div class="footer-container">
    <div class="button-container">
      <div @click="goUp" class="go-up-button">
        <span class="up">UP</span>
        <div v-if="isVideo" class="up-icon">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M9.23608 9.23608L22.4305 22.4305" stroke="black" stroke-width="1.5" stroke-linejoin="round"/>
            <path d="M22.4305 9.23608V22.4305H9.23608" stroke="black" stroke-width="1.5" stroke-linecap="square" stroke-linejoin="round"/>
          </svg>
        </div>
        <div v-else class="up-icon">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M9.23608 9.23608L22.4305 22.4305" stroke="white" stroke-width="1.5" stroke-linejoin="round"/>
            <path d="M22.4305 9.23608V22.4305H9.23608" stroke="white" stroke-width="1.5" stroke-linecap="square" stroke-linejoin="round"/>
          </svg>
        </div>
      </div>
    </div>
    <hr>
    <div class="copy">
      &copy;  2023 - Xavi Florit Pons
    </div>
  </div>
</template>

<script>
  export default {
    name: "WebFooter",

    props: {
      isVideo: {
        type: Boolean,
        default: false
      }
    },

    methods: {
      goUp() {
        window.scrollTo({top: 0, behavior: 'smooth'});
      }
    }
  }
</script>

<style lang="less">
.footer-container {
  background: white;
  width: 100%;
  position: relative;
  bottom: 0;
  z-index: 30;
  font-size: .8rem;

  .go-up-button {
    display: none;
  }

  hr {
    border: 1px solid rgb(235, 235, 235);
  }

  &.yea {
    position: fixed;
  }

  &.is-video {
    background-color: #141414;
    color: white;

    hr {
      border: 1px solid rgb(105, 105, 105);
    }
  }
}

@media (max-width: 768px) {
  .footer-container {

    .button-container {
      padding: 0 30px;
      display: flex;
      justify-content: flex-end;

      .go-up-button {
        font-size: 18px;
        color: white;
        display: flex;
        background-color: #141414;
        width: fit-content;
        margin: 4rem 0;
        padding: 2rem 1.7rem 2rem 2rem;
  
        .up-icon {
          margin-left: .5rem;
          transform: rotate(180deg);
        }
      }
    }

    &.yea {
      position: relative;
    }

    &.is-video {
      .button-container {
        .go-up-button {
          background-color: white;
          color: #141414;
        }
      }
    }
  }
}
</style>