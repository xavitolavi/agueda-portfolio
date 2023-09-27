<template>
  <div class="mobile-menu-container">
    <div class="section-selector">
      <div 
        v-for="section in sections" 
        @click="selectSection(section.type)"
        :key="'section_' + section.type"
        class="section" 
      >
        <span> {{ section.name }}</span>
      </div>
    </div>
    <div class="menu-actions">
      <div @click="$emit('select-cv', true)" class="action">
        <span class="button-text">CV</span>
        <div class="icon">
          <svg width="36" height="36" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M9.23608 9.23608L22.4305 22.4305" stroke="white" stroke-width="1.5" stroke-linejoin="round"/>
              <path d="M22.4305 9.23608V22.4305H9.23608" stroke="white" stroke-width="1.5" stroke-linecap="square" stroke-linejoin="round"/>
            </svg>
        </div>
      </div>
      <div class="action">
        <a href="mailto:name@rapidtables.com?subject=The%20subject%20of%20the%20mail">
          <span class="button-text">CONTACT</span>
          <div class="icon">
            <svg width="36" height="36" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M9.23608 9.23608L22.4305 22.4305" stroke="white" stroke-width="1.5" stroke-linejoin="round"/>
              <path d="M22.4305 9.23608V22.4305H9.23608" stroke="white" stroke-width="1.5" stroke-linecap="square" stroke-linejoin="round"/>
            </svg>
          </div>
        </a>
      </div>
    </div>
    <div class="social-actions">
      <a href="https://www.instagram.com/nuggetilla/">INSTAGRAM</a>
      <a href="https://www.linkedin.com/in/%C3%A0gueda-gol-617349177/">LINKEDIN</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MobileMenu',

  data() {
    return {
      sections: [
        { type: "illustration", name: "illustration" },
        { type: "design", name: "ux/ui design" },
        { type: "video", name: "videography" }
      ],
      buttons: [{
        text: 'cv',
        action: 'select-cv'
      }, {
        text: 'contact',
        action: 'open-email',
      }],
    }
  },

  methods: {
    selectSection(section) {
      this.$emit('select-section', section);
    },
  }
}
</script>

<style lang="less">
.mobile-menu-container {
  margin-top: 250px;
  font-size: 24px;
  text-transform: uppercase;
  color: #fff;

  a {
    color: #fff;
  }

  .section {
    margin-bottom: 2rem;

    &:active {
      font-weight: bold;
    }
  }

  .menu-actions {
    margin-top: 8rem;

    .action, a {
      display: flex;
      justify-content: center;
      text-align: end;
    }
  }

  .social-actions {
    margin-top: 8rem;

    a {
      margin-right: 2rem;
      font-size: 16px;
    }
  }
}
</style>