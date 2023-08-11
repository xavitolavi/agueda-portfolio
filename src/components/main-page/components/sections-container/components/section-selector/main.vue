<template>
    <div class="section-selector">
        <div 
            v-for="section in sections"
            :key="'section_' + section.type"
            :class="sectionClasses(section.type)"
            class="portfolio-section"
            @click="selectSection(section.type)"
        >
            <span> {{ section.name }}</span>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'SectionSelector',

        props: {
            selectedSection: {
                type: String,
                default() {
                    return null;
                }
            },
        },

        data() {
            return {
                sections: [
                    {type: "illustration", name: "illustration"},
                    {type: "design", name: "ux/ui design"},
                    {type: "video", name: "videography"}
                ]
            }
        },

        methods: {
            selectSection(section) {
                this.$emit('section-select', section);
            },

            sectionClasses(section) {
                return {selected: this.selectedSection === section};
            }
        },
    }
</script>

<style lang="less">
.section-selector {
    display: flex;
    flex-direction: column;
    margin-left: 60px;
    text-align: justify;
    width: max-content;
    
    .portfolio-section {
        width: max-content;
        cursor: pointer;
        text-transform: uppercase;
    }

    .portfolio-section:hover {
        font-weight: bold;
    }

    .portfolio-section.selected {
        font-weight: bold;
        text-decoration: line-through;
    }
}
</style>