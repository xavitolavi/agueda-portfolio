<template>
  <div class="header-container" :class="[isActive, {'is-video' : isVideo}]">
    <div class="header-logo" @click="$emit('select-section', null)">
      <svg v-if="isVideo || menuOpen" width="41" height="50" viewBox="0 0 41 50" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M38.836 49.708C38.308 49.708 37.864 49.528 37.504 49.168C37.168 48.808 37 48.364 37 47.836C37 47.308 37.168 46.876 37.504 46.54C37.864 46.18 38.308 46 38.836 46C39.34 46 39.76 46.18 40.096 46.54C40.456 46.876 40.636 47.308 40.636 47.836C40.636 48.364 40.456 48.808 40.096 49.168C39.76 49.528 39.34 49.708 38.836 49.708Z" fill="white"/>
        <path d="M12.6141 29.5621L11.2436 33.3178L11.1652 33.5324L22.0805 33.5333L20.6414 29.5621H12.6141Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M5.25087 49.7352C5.25087 49.7352 7.11769 44.6668 8.31387 41.4192C8.86924 39.8687 9.18061 38.9994 9.73598 37.449C10.2941 35.9195 11.1652 33.5324 11.1652 33.5324L11.2436 33.3178L12.6141 29.5621L16.6277 18.5635L20.6414 29.5621L22.0805 33.5333L23.5195 37.449L24.9416 41.4192L28.0046 49.7352H33.2555L19.5267 12.5545H13.7835L0 49.7352H5.25087ZM21.988 10.3548V6.70648L10.3376 0V4.23849L21.988 10.3548Z" fill="white"/>
      </svg>
      <svg v-else width="41" height="50" viewBox="0 0 41 50" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M38.836 49.708C38.308 49.708 37.864 49.528 37.504 49.168C37.168 48.808 37 48.364 37 47.836C37 47.308 37.168 46.876 37.504 46.54C37.864 46.18 38.308 46 38.836 46C39.34 46 39.76 46.18 40.096 46.54C40.456 46.876 40.636 47.308 40.636 47.836C40.636 48.364 40.456 48.808 40.096 49.168C39.76 49.528 39.34 49.708 38.836 49.708Z" fill="black" />
        <path d="M12.6141 29.5621L11.2436 33.3178L11.1652 33.5324L22.0805 33.5333L20.6414 29.5621H12.6141Z" fill="black" />
        <path fill-rule="evenodd" clip-rule="evenodd" d="M5.25087 49.7352C5.25087 49.7352 7.11769 44.6668 8.31387 41.4192C8.86924 39.8687 9.18061 38.9994 9.73598 37.449C10.2941 35.9195 11.1652 33.5324 11.1652 33.5324L11.2436 33.3178L12.6141 29.5621L16.6277 18.5635L20.6414 29.5621L22.0805 33.5333L23.5195 37.449L24.9416 41.4192L28.0046 49.7352H33.2555L19.5267 12.5545H13.7835L0 49.7352H5.25087ZM21.988 10.3548V6.70648L10.3376 0V4.23849L21.988 10.3548Z" fill="black" />
      </svg>
    </div>
    <div class="header-buttons">
      <header-buttons 
        v-for="(button, index) in buttons" 
        @select-cv="$emit('select-cv', $event)"
        class="desktop-main-buttons"
        :key="'btn' + index" 
        :text="button.text" 
        :action="button.action"
        :selected-cv="selectedCv" 
        :is-video="isVideo"
      />
      <div class="burger-menu" @click="handleMenu">
        <svg v-if="!menuOpen" width="24" height="28" viewBox="0 0 24 28" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M3 14.1866H21" :stroke="strokeColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M3 7.35205H21" :stroke="strokeColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M3 21.0211H21" :stroke="strokeColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
        <svg v-else width="24" height="28" viewBox="0 0 18 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M2.25 18L15.75 6" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M2.25 6L15.75 18" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
import HeaderButtons from './buttons/main.vue';

export default {

  name: 'PortfolioHeader',

  components: {
    HeaderButtons
  },

  props: {
    selectedCv: {
      type: Boolean,
      default: false
    },

    menuOpen: {
      type: Boolean,
      default: false
    },

    isVideo: {
      type: Boolean,
      default: false
    },
  },

  data() {
    return {
      buttons: [{
        text: 'cv',
        action: 'select-cv'
      }, {
        text: 'contact',
        action: 'open-email',
      }],
      active: false
    }
  },

  methods: {
    handleMenu() {
      this.active = !this.menuOpen;

      this.$emit('open-burger-menu', this.active);
    }
  },

  computed: {
    isActive() {
      if (this.menuOpen) {
				return 'active';
			}

			return '';
    },

    strokeColor() {
      if (this.isVideo) {
        return 'white';
      }

      return 'black';
    }
  }
}

</script>

<style lang="less">
.header-container {
  position: fixed;
  top: 0;
  width: 100%;
  display: flex;
  justify-content: space-between;
  padding-top: 20px;
  background: white;
  z-index: 20;
  height: 80px;

  &.is-video {
    background-color: #141414;
  }

  .header-logo {
    cursor: pointer;
    padding-left: 60px;
  }

  .header-buttons {
    display: flex;
    flex-direction: row;
    height: fit-content;
    padding-right: 60px;

    .burger-menu {
      display: none;
    }
  }

  &.active {
    background-color: #141414;
  }
}

@media (max-width: 768px) {
  .header-container {

    .header-logo {
      padding-left: 30px;
    }

    .header-buttons {
      padding-right: 30px;

      .desktop-main-buttons {
        display: none;
      }

      .contact-button a {
        margin-right: 6px;
      }

      .burger-menu {
        display: block;
        margin-top: 1rem;
        cursor: pointer;
      }
    }
  }
}
</style>