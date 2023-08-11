<template>
    <div class="sections-container">
        <section-selector 
            @section-select="$emit('section-select', $event)"
            :selected-section="selectedSection"
        />
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
import SectionSelector from './components/section-selector/main.vue';
import SectionView from './components/section-view/main.vue';

    export default {
        name: "SectionsContainer",

        components: {
            SectionSelector,
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
    position: relative;
}

</style>