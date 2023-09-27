<template>
  <div class="app-container">
    <div v-if="pageFullyLoaded">
      <div v-if="!gifAnimationDone" class="loading-animation-container">
      </div>
      <div v-else class="app-content" :class="{ 'show-content': gifAnimationDone }">
        <Header
          @select-section="selectSection"
          @select-cv="selectCV"
          @open-burger-menu="openBurgerMenu"
          :selected-cv="selectedCv"
          :menu-open="menuOpen"
          :is-video="isVideo"
        />
        <div v-if="menuOpen" class="mobile-menu">
          <MobileMenu 
            @select-section="selectSection"
            @select-cv="selectCV"
          />
        </div>
        <div v-else class="main">
          <SectionSelector
            v-if="!selectedCv"
            @section-select="selectSection"
            @project-select="selectProject"
            :selected-section="selectedSection"
            :selected-project="selectedProject"
            :is-video="isVideo"
          />
          <MainPage 
            @section-select="selectSection"
            @project-select="selectProject"
            :selected-section="selectedSection"
            :section-projects="sectionProjects"
            :projects="projects"
            :selected-project="selectedProject"
            :selected-cv="selectedCv"
            :is-video="isVideo"
          />
          <Footer 
            v-if="!selectedSection"
            :is-video="isVideo"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/header/main.vue';
import MainPage from './components/main-page/main.vue';
import SectionSelector from './components/section-selector/main.vue';
import projectSchema from './components/main-page/components/sections-container/components/section-view/components/section/data/project-schema';
import Footer from './components/footer/main.vue';
import MobileMenu from './components/mobile-menu/main.vue';

export default {
  name: 'App',

  components: {
    Header,
    MainPage,
    SectionSelector,
    Footer,
    MobileMenu
  },

  data() {
    return {
      selectedSection: "",
      projects: [],
      sectionProjects: [],
      selectedProject: {},
      selectedCv: false,
      gifAnimationDone: false,
      pageFullyLoaded: false,
      menuOpen: false
    }
  },

  created() {
    this.setAllProjects();
  },

  mounted() {
    document.onreadystatechange = () => {
      if (document.readyState === "complete") {
        this.pageFullyLoaded = true;

        setTimeout(() => {
          this.gifAnimationDone = true;
        }, 4030);
      }
    }
  },

  computed: {
    isVideo() {
      let root = document.documentElement;

      if (this.selectedSection === 'video') {
        root.classList.add('is-video');
      } else {
        root.classList.remove('is-video');
      }

      return this.selectedSection === 'video';
    }
  },

  methods: {
    selectCV(status) {
      window.scrollTo(0,0);
      this.menuOpen = false;
      this.selectedCv = status;
    },

    selectSection(section) {
      window.scrollTo(0,0);
      this.menuOpen = false;
      this.selectedCv = false;
      this.selectedProject = null;
      this.sectionManagement(section);
    },

    selectProject(project) {
      window.scrollTo(0,0);
      this.selectedProject = project;
      this.menuOpen = false;

      if (project) {
        if (typeof project === 'object') {
          this.sectionManagement(this.selectedProject.type)
          this.selectedProject = this.sectionProjects.find(project => project.id === this.selectedProject.id);
        } else {
          this.selectedProject = projectSchema.find(p => p.id === project);
          this.sectionManagement(this.selectedProject.type)
        }
      }
    },

    sectionManagement(section) {
      this.selectedSection = section;

      this.sectionProjects = this.projects.filter(project => {
        return project.type === this.selectedSection;
      })

      this.sectionProjects = this.sectionProjects.map(project => {

        let schemaProject = projectSchema.find(schema => {
          return schema.id === project.id
        });

        return { ...project, ...schemaProject }
      })
    },

    setAllProjects() {
      let illustrations = require.context(
        '@/assets/images_lower',
        true,
        /^.*\.jpg$/
      )

      this.projects = illustrations.keys();

      this.projects = this.projects.map(img => {
        return img.replace('./', '');
      })

      this.projects = this.projects.map(project => {
        return {
          type: project.substring(0, project.lastIndexOf('_')).split('_')[1],
          img: project,
          id: project.split('_')[0]
        }
      })
    },

    openBurgerMenu(isOpen) {
      this.menuOpen = isOpen;
    },
  }
}
</script>

<style lang="less">
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;300;400;600;700&display=swap');

#app {
  font-family: Poppins, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
}

html {
  position: relative;
  min-height: 100%;

  &.is-video {
    background-color: #141414;
  }
}

body {
  display: block;
}

* {
  margin: 0;
  padding: 0;
  border: 0;
  outline: 0;
  text-decoration: none;
  list-style: none;
}

.loading-animation-container {
  z-index: 50;
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  background: url("@/assets/animation/opening-animation.gif") no-repeat center;
  background-size: cover;
}

.app-content {
  opacity: 0;
  transition: opacity 1s ease;

  &.show-content {
    opacity: 1;
  }

  .mobile-menu {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    background-color: #141414;
  }
}
</style>
