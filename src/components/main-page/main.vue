<template>
  <div class="main-page">
    <div v-if="selectedCv" class="cv-container">
      <curriculum-view />
    </div>
    <div v-else class="main-container">
      <sections-container 
        @section-select="$emit('section-select', $event)"
        @project-select="$emit('project-select', $event)" 
        :selected-section="selectedSection"
        :section-projects="sectionProjects" 
        :selected-project="selectedProject"
        :is-video="isVideo"
      />
      <all-projects v-if="!selectedSection" 
        @project-select="$emit('project-select', $event)" 
        :projects="projects"
      />
    </div>
  </div>
</template>

<script>
import SectionsContainer from './components/sections-container/main.vue';
import AllProjects from './components/all-projects/main.vue';
import CurriculumView from '../curriculum/main.vue';

export default {
  name: 'MainPage',

  components: {
    SectionsContainer,
    AllProjects,
    CurriculumView
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

    projects: {
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

    selectedCv: {
      type: Boolean,
      default: false
    },

    isVideo: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="less">
.main-page {

  .main-container {
    margin-top: 225px;
    position: sticky;
    background: white;
    z-index: 10;
  }

  .go-up-button {
    display: none;
  }
}

@media (max-width: 650px) {
  .main-page {

    .main-container {
      margin-top: 225px;
    }

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
  }
}
</style>