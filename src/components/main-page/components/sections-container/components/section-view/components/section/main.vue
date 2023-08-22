<template>
  <div class="selected-section-container">
    <div 
      v-if="!selectedProject" 
      class="selected-section-slider" 
      :class="grabActive" :ref="'slider'"
      @dragstart="mouseDown" 
      @dragend="mouseUp" 
      @drag="mouseMove"
    >
      <div 
        v-for="(project, index) in sectionProjects" 
        :key="'section_project_' + index" 
        class="project"
      >
        <img 
          :src="require('@/assets/images_lower/' + project.img)" 
          :alt="'section_project_' + index"
          @click="handleClick(project)"
        >
        <span class="title">{{ project.title}}</span>
        <span>{{ project.subtitle }}</span>
      </div>
    </div>
    <div v-else class="selected-project">
      <component 
        :is="getComponent(selectedProject)"
        :selected-project="selectedProject"
        :ref="selectedProject.component + '_component'"
        :key="selectedProject.id"
      />
    </div>
  </div>
</template>

<script>
import Nuggetilla from './components/project/components/nuggetilla.vue';
import LaBodegueta from './components/project/components/la-bodegueta.vue';
import VolverASerYo from './components/project/components/volver-a-ser-yo.vue';
import GaudeixLaFesta from './components/project/components/gaudeix-la-festa.vue';
import Champagne from './components/project/components/champagne.vue';
import RegalJan from './components/project/components/regal-jan.vue';
import Cwork from './components/project/components/cwork.vue';
import EnricGol from './components/project/components/enric-gol.vue';
import Mediatics from './components/project/components/mediatics.vue';
import ImDigital from './components/project/components/im-digital.vue';


export default {
  name: 'CurrentSection',

  components: {
    Nuggetilla,
    LaBodegueta,
    VolverASerYo,
    GaudeixLaFesta,
    Champagne,
    RegalJan,
    Cwork,
    EnricGol,
    Mediatics,
    ImDigital
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
    }
  },

  data() {
    return {
      isDown: false,
      startX: null,
      scrollLeft: null,
      projects: []
    }
  },

  methods: {
    mouseDown(e) {
      this.isDown = true;
      this.startX = e.pageX - this.$refs['slider'].offsetLeft;
      this.scrollLeft = this.$refs['slider'].scrollLeft;
    },

    mouseUp() {
      this.isDown = false;
    },

    mouseMove(e) {
      if (!this.isDown) {
        return;
      }

      e.preventDefault();
      const x = e.pageX - this.$refs['slider'].offsetLeft;
      const walk = (x - this.startX) * 1.5; //scroll-fast
      this.$refs['slider'].scrollLeft = this.scrollLeft - walk;
    },

    handleClick(project) {
      this.$emit('project-select', project)
    },

    getComponent(project) {
      return project.component;
    }
  },

  computed: {
    grabActive() {
      if (this.isDown) {
        return "active";
      }

      return "";
    },

  }
}
</script>

<style lang="less">
.selected-section-slider {
  display: flex;
  flex-direction: row;
  position: relative;
  overflow-x: hidden;
  overflow-y: hidden;
  white-space: nowrap;
  transition: all 0.2s;
  will-change: transform;
  user-select: none;
  cursor: pointer;
  padding-left: 20rem;

  .project {
    display: flex;
    flex-direction: column;

    img {
      width: 40rem;
      margin-right: 20px;
    }

    span {
      text-align: left;
      text-transform: uppercase;

    }
 
    .title {
      font-weight: 600;
    }
  }
}

.selected-section-slider.active {
  background: rgba(255, 255, 255, 0.3);
  cursor: grabbing;
  cursor: -webkit-grabbing;
  transform: scale(1);
}
</style>