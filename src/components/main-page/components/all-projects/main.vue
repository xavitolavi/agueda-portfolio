<template>
    <div class="all-projects-container">
        <div class="images-container">
            <div 
                v-for="(project, index) in projects"
                class="image"
                :style="`background-image: url(${getImageUrl(project)})`"
                :key="'project_' + index"
                :alt="'project_' + index"
                @click="$emit('project-select', project)"
            />
            <img 
                v-for="(project, index) in projects"
                :key="'project_' + index"
                :src="require('@/assets/images_lower/' + project.img)"
                :alt="'project_' + index"
                @click="$emit('project-select', project)"
            >
        </div>
    </div>
</template>

<script>
    export default {

        name: "AllProjects",

        props: {
            projects: {
                type: Array,
                default() {
                    return []
                }
            }
        },

        methods: {
            getImageUrl(project) {
                console.log(`/assets/images_lower/${project.img}`);
                return `assets/images_lower/${project.img}`
            }
        }
    }
</script>

<style lang="less">
.all-projects-container {
    padding: 60px;
    max-width: 100%;
    position: relative;

    .images-container {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
        grid-template-rows: repeat(auto-fit, 230px);
        grid-gap: 1rem;
        grid-auto-flow: dense;

        img,image {
            cursor: pointer;
            width: 100%;
            height: 100%;
        }
    }
}

</style>