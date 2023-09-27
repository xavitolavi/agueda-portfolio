<template>
  <div class="selected-section-container" :class="{'is-video' : isVideo}">
    <div 
      v-if="!selectedProject" 
      class="selected-section-slider" 
      :class="grabActive" 
      :ref="'slider'"
      @mousedown="mouseDown"
    >
      <div class="slider-container mobile" :style="leftSlider">
        <div 
          v-for="(project, index) in sectionProjects" 
          :key="'section_project_' + index" 
          class="project"
        >
          <img :src="require('@/assets/images_lower/' + project.img)" :alt="project.id">
          <span class="title">{{ project.title }}</span>
          <span>{{ project.subtitle }}</span>
        </div>
      </div>
    </div>
    <div v-else class="selected-project">
      <component 
        :is="getComponent(selectedProject)" 
        :selected-project="selectedProject"
        :ref="selectedProject.component + '_component'" 
        :key="selectedProject.id"
        :is-video="isVideo"
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
import SaLluna from './components/project/components/sa-lluna.vue';


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
    ImDigital,
    SaLluna
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

  created() {
    this.left = 0
  },

  data() {
    return {
      isDown: false,
      startX: null,
      scrollLeft: null,
      projects: [],
      left: 0,
      lastPosition: 0,
      sliderWidth: 0
    }
  },

  watch: {
    selectedSection() {
      this.left = 0;
    }
  },

  methods: {
    mouseDown(e) {
      e.preventDefault();

      this.start = performance.now();
      this.drag = true;
      this.startX = e.pageX;

      this.lastPosition = e.pageX;
      
      this._dragCallback = (e) => {
        this.left = this.left - (this.lastPosition - e.pageX)
        this.lastPosition = e.pageX;

        if (this.selectedSection === 'illustration') {
          if (this.left <= -3500) {
            this.left = -3499;
          }
        } else {
          if (this.left <= -600) {
            this.left = -599;
          }
        }

        if (this.left >= 0) {
          this.left = -1;
        }
      }

      this._mouseUpCallback = () => {
        if (performance.now() - this.start <= 100) {
          if (e.target.__vnode.props.alt) {
            this.handleClick(e.target.alt)
          }
        }
        window.removeEventListener("mousemove", this._dragCallback);
        window.removeEventListener("mouseup", this._mouseUpCallback);
      }

      window.addEventListener("mousemove", this._dragCallback);
      window.addEventListener("mouseup", this._mouseUpCallback);
    },

    handleClick(project) {
      this.$emit('project-select', project)
    },

    getComponent(project) {
      return project.component;
    },
    
    handleBack() {
      if (this.selectedProject) {
        this.$emit('project-select', null);
      } else {
        this.$emit('section-select', null)
      }
    }
  },

  computed: {
    grabActive() {
      if (this.isDown) {
        return "active";
      }

      return "";
    },

    leftSlider() {
      return `margin-left : ${this.left}px`
    },

    isVideo() {
      return this.selectedSection === 'video';
    }
  }
}
</script>

<style lang="less">
.selected-section-container {

  .mobile-actions {
    display: none;
  }

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
    padding-left: 17rem;

    .slider-container {
      display: flex;
      flex-direction: row;
    }

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

  .selected-project {
    max-height: max-content;
    padding: 0 17rem;
    margin-bottom: 5rem;

  }

  .selected-section-slider.active {
    background: rgba(255, 255, 255, 0.3);
    cursor: grabbing;
    cursor: -webkit-grabbing;
    transform: scale(1);
  }
}

@media (max-width: 1280px) {
  .selected-section-container {

    .selected-section-slider {
      padding: 0 13rem;

      .project img { 
        width: 35rem;
      }
    }

    .selected-project {
      max-height: max-content;
      padding: 0 10rem 0 13rem;
      margin-bottom: 5rem;
    }
  }
}

@media (max-width: 768px) {
  .selected-section-container {

    .selected-section-slider {
      padding: 0 30px;
      .slider-container {
        display: block;

        &.mobile {
          .project {
            margin-bottom: 1rem;
            width: 100%;

            img {
              width: 100%;
            }
          }

          span {
            display: none;
          }
        }
      }
    }


    .selected-project {
      max-height: max-content;
      padding: 0 30px;
      margin-bottom: 5rem;

    }
  }
}
</style>