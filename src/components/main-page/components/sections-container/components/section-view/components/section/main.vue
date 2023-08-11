<template>
    <div class="selected-project-container">
        <div 
            v-if="!selectedProject"
            class="selected-section-slider"
            :class="grabActive"
            :ref="'slider'"
            @mousedown="mouseDown"
            @mouseleave="mouseLeave"
            @mouseup.prevent="mouseUp"
            @mousemove="mouseMove"
        >
            <img 
                v-for="(project, index) in sectionProjects"
                :key="'section_project_' + index"
                :src="require('@/assets/0_home/' + project.img)"
                :alt="'section_project_' + index"
                @click="$emit('project-select', project)"
            >
        </div>
        <div v-else 
            class="selected-project"
        >
            <selected-project
                :selected-project="selectedProject"
            />
        </div>
    </div>
</template>

<script>
import SelectedProject from './components/project/main.vue';

    export default {
        name: 'CurrentSection',

        components: {
            SelectedProject
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

        data() {
            return {
                isDown: false,
                startX: null,
                scrollLeft: null
            }
        },

        methods: {
            mouseDown(e) {
                this.isDown = true;
                this.startX = e.pageX - this.$refs['slider'].offsetLeft;
                this.scrollLeft = this.$refs['slider'].scrollLeft;
            },

            mouseLeave() {
                this.isDown = false;
            },

            mouseUp() {
                this.isDown = false;
            },

            mouseMove(e) {
                if(!this.isDown) {
                    return;
                }

                e.preventDefault();
                const x = e.pageX - this.$refs['slider'].offsetLeft;
                const walk = (x - this.startX) * 1; //scroll-fast
                this.$refs['slider'].scrollLeft = this.scrollLeft - walk;
            }
        },

        computed: {
            grabActive() {
                if (this.isDown) {
                    return "active";
                }

                return "";
            }
        }
    }
</script>

<style lang="less">

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

    img {
        width: 40rem;
        margin-right: 20px;
    }
}

.selected-section-slider.active {
    background: rgba(255,255,255,0.3);
    cursor: grabbing;
    cursor: -webkit-grabbing;
    transform: scale(1);
  }
</style>