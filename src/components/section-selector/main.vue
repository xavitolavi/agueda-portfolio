<template>
  <div class="section-selector-container">
    <div class="description">
      Hi! My name is <span>Agueda Gol.</span> I'm an <span>illustrator,<br> UX-UI designer, and video editor,
      </span> based in<br> <span>Spain,</span> and this is my portfolio <span>website! :)</span>
    </div>
    <div class="section-selector">
      <div v-for="section in sections" :key="'section_' + section.type" :class="sectionClasses(section.type)"
        class="portfolio-section" @click="selectSection(section.type)">
        <span> {{ section.name }}</span>
      </div>
      <div v-if="selectedSection || selectedProject" class="back-button" @click="handleBack">
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
        return {};
      }
    },
  },

  data() {
    return {
      sections: [
        { type: "illustration", name: "illustration" },
        { type: "design", name: "ux/ui design" },
        { type: "video", name: "videography" }
      ]
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
        this.$emit('project-select', null)
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


  .description {
    margin-left: 60px;
    margin-top: 50px;
    text-align: justify;
    color: rgba(0, 0, 0, .5);

    span {
      color: #000000;
    }
  }

  .section-selector {
    display: flex;
    flex-direction: column;
    margin-top: 60px;
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
      margin-left: 20rem;
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
</style>