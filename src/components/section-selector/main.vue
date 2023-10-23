<template>
  <div class="section-selector-container" :class="{'is-video' : isVideo}">
    <div class="description desktop">
      Hi! My name is <span>Agueda Gol.</span> I'm an <span>illustrator,<br class="mobile"> UX-UI designer, and video editor,
      </span> based in<br class="mobile"> <span>Spain,</span> and this is my portfolio <span>website!</span>
    </div>
    <div v-if="!selectedSection" class="description mobile">
      Hi! My name is <span>Agueda Gol.</span> I'm an <span>illustrator,<br class="mobile"> UX-UI designer, and video editor,
      </span> based in<br class="mobile"> <span>Spain,</span> and this is my portfolio <span>website!</span>
    </div>
    <div v-if="selectedSection" class="mobile-actions">
      <span class="mobile-title"> {{ getTitle }} </span>
      <span @click="handleBack" class="back-button-mobile">{{ getBackButton }}</span>
    </div>
    <div class="section-selector">
      <div 
        v-for="section in sections" 
        @click="selectSection(section.type)"
        :key="'section_' + section.type"
        :class="sectionClasses(section.type)"
        class="portfolio-section" 
      >
        <span> {{ section.name }}</span>
      </div>
      <div 
        v-if="selectedSection || selectedProject" 
        @click="handleBack"
        class="back-button" 
      >
        <svg class="arrow-icon" width="24" height="28" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M5.83398 5.83331L14.1673 14.1666" stroke="black" stroke-linejoin="round" />
          <path d="M14.1673 5.83331V14.1666H5.83398" stroke="black" stroke-linecap="square" stroke-linejoin="round" />
        </svg>
        <span class="button"> {{ getButtonText }} </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SectionSelector',

  props: {
    selectedSection: {
      type: String,
      default() {
        return null;
      }
    },

    selectedProject: {
      type: Object,
      default() {
        return null;
      }
    },

    isVideo: {
      type: Boolean,
      default: false
    }
  },

  created() {
    this.currentSection = this.selectedSection;
  },

  data() {
    return {
      sections: [
        { type: "illustration", name: "illustration" },
        { type: "design", name: "ux/ui design" },
        { type: "video", name: "videography" }
      ],
      currentSection: null
    }
  },

  computed: {
    getButtonText() {
      if (this.selectedSection && this.selectedProject) {
        return "Back";
      }

      if (this.selectedSection) {
        return "All Projects";
      }

      return "";
    },

    getTitle() {
      if (this.selectedProject) {
        return this.selectedProject.title;
      } else {
        return this.selectedSection;
      }
    },

    getBackButton() {
      if (this.selectedSection && this.selectedProject) {
        return "Go back";
      }

      if (this.selectedSection) {
        return "All Projects";
      }

      return "";
    }
  },

  methods: {
    selectSection(section) {
      this.$emit('section-select', section);
    },

    sectionClasses(section) {
      return { selected: this.selectedSection === section };
    },

    handleBack() {
      if (this.selectedProject) {
        this.$emit('project-select', null);
      } else {
        this.$emit('section-select', null)
      }
    }
  },
}
</script>

<style lang="less">
.section-selector-container {
  position: fixed;
  width: 100%;
  top: 80px;
  background: white;
  z-index: 20;
  padding-bottom: 20px;

  &.is-video {
    background-color: #141414;
    color: white;

    .description {
      color: white;

      span {
        color: grey;
      }
    }

    .section-selector .back-button {
      background-color: #141414;
    }
  }

  .mobile-actions {
    display: none;
  }

  .description {
    margin-left: 60px;
    margin-top: 1.5rem;
    text-align: justify;
    color: rgba(0, 0, 0, .5);

    &.desktop {
      display: block;
    }

    &.mobile {
      display: none;
    }

    span {
      color: #000000;
    }
  }

  .section-selector {
    display: flex;
    flex-direction: column;
    margin-top: 1.5rem;
    margin-left: 60px;
    text-align: justify;
    width: max-content;

    .portfolio-section {
      width: max-content;
      cursor: pointer;
      text-transform: uppercase;
      transition: .1s all ease-in-out;
    }

    .portfolio-section:hover {
      font-weight: bold;
    }

    .portfolio-section.selected {
      font-weight: bold;
      text-decoration: line-through;
      transition: .1s all ease-in-out;
    }

    .back-button {
      position: absolute;
      left: 0;
      bottom: 0;
      margin-left: 22rem;
      background: white;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: .05s all ease-in-out;

      .arrow-icon {
        transform: rotate(180deg);
        display: none;
      }

      .button {
        padding-top: 3px;
        font-style: italic;
        text-transform: uppercase;
      }

      &:hover {
        cursor: pointer;
        font-weight: bold;

        .arrow-icon {
          display: block;
        }
      }
    }
  }
}

@media (min-width: 1500px) {
  .section-selector-container {
    .section-selector {
      .back-button {
        margin-left: 30rem;
      }
    }
  }
}

@media (max-width: 1280px) {
  .section-selector-container {
    .section-selector {
      .back-button {
        margin-left: 13rem;
      }
    }
  }
}

@media (max-width: 768px) {
  .section-selector-container {
    .mobile-actions {
      padding: 0 30px;
      display: flex;
      margin-top: 6rem;
      justify-content: space-between;

      .mobile-title {
        text-transform: uppercase;
        font-weight: 400;
        font-size: 18px;
        text-align: start;
        width: 70%;
      }

      .back-button-mobile {
        cursor: pointer;
        text-decoration: underline;
        font-style: italic;
      }
    }

    .description {
      text-align: center;
      margin-left: 0;
      padding: 0 40px;

      &.desktop {
        display: none;
      }

      &.mobile {
        padding-top: 2rem;
        display: block;
      }
    }

    .section-selector {
      display: none;
    }
  }
}

@media (max-width: 450px) {
  .section-selector-container {
    .description {

      .mobile {
        display: none;
      }
    }
  }
}
</style>