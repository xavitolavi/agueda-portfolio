<template>
    <div class="main-container">
        <sections-container
            @section-select="$emit('section-select', $event)"
            @project-select="$emit('project-select', $event)"
            :selected-section="selectedSection"
            :section-projects="sectionProjects"
            :selected-project="selectedProject"
        />
        <all-projects 
            v-if="!selectedSection"
            @project-select="$emit('project-select', $event)"
            :projects="projects"
        />
    </div>
</template>

<script>
import SectionsContainer from './components/sections-container/main.vue';
import AllProjects from './components/all-projects/main.vue';

    export default {
        name: 'MainPage',

        components: {
            SectionsContainer,
            AllProjects
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
        }
    }
</script>

<style lang="less">

.main-container {
    margin-top: 100px;
}
</style>