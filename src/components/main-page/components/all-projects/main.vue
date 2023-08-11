<template>
    <div class="all-projects-container">
        <div class="images-container">
            <img 
                v-for="(project, index) in projects"
                :key="'project_' + index"
                :src="require('@/assets/0_home/' + project.img)"
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
        grid-template-rows: repeat(3, 230px);
        grid-gap: 1rem;
        grid-auto-flow: dense;

        img {
            cursor: pointer;
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    }
}

</style>