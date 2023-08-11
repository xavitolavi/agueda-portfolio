<template>
    <div class="section-view-container">
        <span class="button" @click="handleBack"> {{ getButtonText }} </span>
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

        computed: {
            getButtonText() {
                console.log(this.selectedSection, this.selectedProject);
                if (this.selectedSection && this.selectedProject) {
                    return "Back";
                }

                if (this.selectedSection) {
                    return "All Projects";
                }

                return "";
            }         
        },

        methods: {
            handleBack() {
                if (this.selectedProject) {
                    this.$emit('project-select', null)
                } else {
                    this.$emit('section-select', null)
                }
            }
        }

    }
</script>

<style lang="less">

.section-view-container {
    margin-top: 4rem;
    margin-left: 20rem;
    display: flex;
    flex-direction: column;
    align-items: start;
    max-width: 100%;
    left: 0;
    right: 0;
    position: absolute;

    .button {
        font-style: italic;
        text-transform: uppercase;
    }
    
    .button:hover {
        cursor: pointer;
        font-weight: bold;
    }

    .selected-section {
        max-width: inherit;
        margin-top: 40px;
    }
}
</style>