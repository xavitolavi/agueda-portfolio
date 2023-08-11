<template>
    <div class="selected-project-container" v-if="selectedProject">
        <img :src="require('@/assets/images_lower/' + selectedProject.img)" :alt="selectedProject.img">
    </div>
</template>

<script>
    export default {
        name: "SelectedProject",

        props: {
            selectedProject: {
                type: Object,
                default() {
                    return {};
                }
            }
        }
    }
</script>

<style lang="less" scoped>
.selected-project-container {
    max-height: max-content;
    img {
        width: 900px;
    }

}
</style>