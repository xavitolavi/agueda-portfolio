<template>
    <div class="section-view-container">
        <div class="selected-section">
            <current-section 
                @project-select="$emit('project-select', $event)"
                :selected-section="selectedSection"
                :section-projects="sectionProjects"
                :selected-project="selectedProject"
            />
        </div>
    </div>
</template>

<script>
import CurrentSection from './components/section/main.vue';

    export default {
        name: "SectionView",

        components: {
            CurrentSection
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
        },

    }
</script>

<style lang="less">

.section-view-container {
    margin-top: 4rem;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    max-width: 100%;
    left: 0;
    right: 0;
    position: absolute;

    .selected-section {
        max-width: inherit;
        margin-top: 40px;
    }
}
</style>