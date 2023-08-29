<template>
  <div class="app-container">
    <div v-if="pageFullyLoaded">
      <div
          v-if="!gifAnimationDone"
          class="loading-animation-container">
      </div>

      <div class="app-content"
         :class="{'show-content': gifAnimationDone}"
        >
        <Header 
          @select-section="selectSection"
          @select-cv="selectCV"
          :selected-cv="selectedCv"
        />
        <SectionSelector 
          v-if="!selectedCv"
          @section-select="selectSection"
          @project-select="selectProject"
          :selected-section="selectedSection"
          :selected-project="selectedProject"
        />
        <MainPage
          :selected-section="selectedSection"
          :section-projects="sectionProjects"
          :projects="projects"
          :selected-project="selectedProject"
          :selected-cv="selectedCv"
          @project-select="selectProject"
        />
        <Footer />
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

export default {
  name: 'App',

  components: {
    Header,
    MainPage,
    SectionSelector,
    Footer
  },

  data() {
      return {
          selectedSection: "",
          projects: [],
          sectionProjects: [],
          selectedProject: {},
          selectedCv: false,
          gifAnimationDone: false,
          pageFullyLoaded: false
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

  methods: {
      selectCV(status) {
        this.selectedCv = status;
      },

      selectSection(section) {
          this.selectedCv = false;
          this.selectedSection = section;
          this.selectedProject = null;

          this.sectionProjects = this.projects.filter(project => {
              return project.type === this.selectedSection;
          })

          this.sectionProjects = this.sectionProjects.map(project => {
            
            let schemaProject = projectSchema.find(schema => {
              return schema.id === project.id
            });

            return {...project, ...schemaProject}
          })
      },

      selectProject(project) {
          this.selectedProject = project;

          if (project) {
            this.selectedSection = project.type;

            this.sectionProjects = this.projects.filter(project => {
              return project.type === this.selectedSection;
            })

            this.sectionProjects = this.sectionProjects.map(project => {
            
              let schemaProject = projectSchema.find(schema => {
                return schema.id === project.id
              });

              return {...project, ...schemaProject}
            })
            
            this.selectedProject = this.sectionProjects.find(project => project.id === this.selectedProject.id);
          }

        },

      setAllProjects() {
          let illustrations = require.context(
              '@/assets/images_lower',
              true,
              /^.*\.png$/
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
      }
  }
}
</script>

<style lang="less">
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;300;600;700&display=swap');

#app {
  font-family: Poppins, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
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
  position: absolute;
  top: 0;
  left: 0;
  height: 100vh;
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
}
</style>
