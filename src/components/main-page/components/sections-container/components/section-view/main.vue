<template>
  <div class="section-view-container">
    <div class="selected-section">
      <current-section 
        @project-select="$emit('project-select', $event)"
        @section-select="$emit('section-select', $event)" 
        :selected-section="selectedSection"
        :section-projects="sectionProjects" 
        :selected-project="selectedProject"
      />
    </div>
    <Footer :is-video="isVideo" :class="footerClasses"/>
  </div>
</template>

<script>
import CurrentSection from './components/section/main.vue';
import Footer from '../../../../../footer/main.vue';

export default {
  name: "SectionView",

  components: {
    CurrentSection,
    Footer
  },

  props: {
    selectedSection: {
      type: String,
      default() {
        return null;
      }
    },

    sectionProjects: {
      type: Array,
      default() {
        return []
      }
    },

    selectedProject: {
      type: Object,
      default() {
        return {};
      }
    },

    isVideo: {
      type: Boolean,
      default: false
    }
  },

  computed: {
    footerClasses() {
      let classes = []; 
      if (!this.selectedProject && this.selectedSection) {
        classes.push("yea");
      }

      if (this.isVideo) {
        classes.push("is-video"); 
      }

      return classes;
    }
  }

}
</script>

<style lang="less">
.section-view-container {
  margin-top: rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  max-width: 100%;
  left: 0;
  right: 0;
  position: absolute;

  .selected-section {
    max-width: inherit;
    margin-top: 60px;
  }
}

@media (max-width: 768px) {
  .section-view-container {
    .selected-section {
      margin-top: 0;
    }
  }
}
</style>