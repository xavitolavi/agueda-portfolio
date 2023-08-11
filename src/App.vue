<template>
  <Header 
    @select-section="selectSection"
  />
  <MainPage 
    @section-select="selectSection"
    @project-select="selectProject"
    :selected-section="selectedSection"
    :section-projects="sectionProjects"
    :projects="projects"
    :selected-project="selectedProject"
  />
</template>

<script>
import Header from './components/header/main.vue';
import MainPage from './components/main-page/main.vue';

export default {
  name: 'App',

  components: {
    Header,
    MainPage
  },

  data() {
      return {
          selectedSection: "",
          projects: [],
          sectionProjects: [],
          selectedProject: {}
      }
  },

  created() {
      this.setAllProjects();
  },

  methods: {
      selectSection(section) {
          this.selectedSection = section;
          this.selectedProject = null;

          this.sectionProjects = this.projects.filter(project => {
            console.log(project.type, this.selectedSection);
              return project.type === this.selectedSection;
          })
      },

      selectProject(project) {
          this.selectedProject = project;

          if (project) {
            this.selectedSection = project.type;

            this.sectionProjects = this.projects.filter(project => {
              return project.type === this.selectedSection;
          })
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
                  type: project.substring(0, project.lastIndexOf('_')),
                  img: project
              }
          })

          console.log(this.projects);
      }
  }
}
</script>

<style>
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
</style>
