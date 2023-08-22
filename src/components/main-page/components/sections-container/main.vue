<template>
    <div class="sections-container">
        <section-view 
            v-if="selectedSection"
            @section-select="$emit('section-select', $event)"
            @project-select="$emit('project-select', $event)"
            :selected-section="selectedSection"
            :section-projects="sectionProjects"
            :selected-project="selectedProject"
        />
    </div>
</template>

<script>
import SectionView from './components/section-view/main.vue';

    export default {
        name: "SectionsContainer",

        components: {
            SectionView
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
        }
    }
</script>

<style lang="less">

.sections-container {
    display: flex;
    flex-direction: row;
    position: sticky;
    top: 220px;
    z-index: 20;
}

</style>