<template>
    <div class="main-page">
        <div 
            v-if="selectedCv"
            class="cv-container"
        >
            <curriculum-view />
        </div>
        <div 
            v-else
            class="main-container"
        >
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
            }
        }
    }
</script>

<style lang="less">

.main-container {
    margin-top: 300px;
    position: sticky;
    background: white;
    z-index: 10;
}
</style>