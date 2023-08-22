<template>
    <div class="curriculum-container">
        <div class="top-container">
            <img src="@/assets/ague-cv.jpg" alt="Ague CV">
            <div class="main-text">
                <p>Hi! I am a passionate illustrator, UX-UI and graphic designer based in Spain. 
                My expertise extends beyond visual arts as I hold a strong background in corporate communication and copywriting. 
                Through my artistic and written skills, I work to create beautiful and purposeful solutions for every project I undertake. 
                Highly commended for my versatility, speed of learning and methodical approach to projects. 
                Capable of working both in team-oriented and independent tasks.</p>
                <p>
                    <ul class="studies">
                        <li><span>2022 - 2023</span>UX UI Design - CODERHOUSE Accademy</li>
                        <li><span>2021 - 2022</span>Graphic design and Web Development - ESPAI</li>
                        <li><span>2017 - 2021</span>Communication and Cultural Industries - UB</li>
                    </ul>
                </p>
                <div class="skills">
                    <ul>
                        <li>English: fluent</li>
                        <li>Catalan: native</li>
                        <li>Spanish: native</li>
                    </ul>
                    <ul>
                        <li>Figma</li>
                        <li>Procreate</li>
                        <li>Wordpress</li>
                        <li>Office Suite</li>
                        <li>Adobe Pr / Id / Ps</li>
                    </ul>
                </div>
            </div>
        </div>
        <div class="bottom-container">
            <ul>
                <li 
                    v-for="exp in experiences"
                    :key="exp.id"
                >
                    <div class="dates">
                        <p>{{ exp.startDate }}</p>
                        <p>{{ exp.endDate }}</p>
                    </div>
                    <div class="place">
                        <p class="title">{{ exp.title }}</p>
                        <p>{{ exp.subtitle }}</p>
                    </div>
                    <div 
                        class="knowledges"
                    >
                        <p 
                            v-for="(skill, index) in exp.skills" 
                            :key="index"
                        >
                            {{ skill }}
                        </p>
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import experiences from './schema';

    export default {
        name: "CurriculumView",

        props: {
            selectedCV: {
                type: Boolean,
                default: () => false
            }
        },

        computed: {
            experiences() {
                return experiences;
            }
        }
    }
</script>

<style lang="less">
.curriculum-container {
    margin: 10rem 8vw 0 8vw;
    display: flex;
    flex-direction: column;

    .top-container {
        display: flex;
        flex-direction: row;
        justify-content: center;
        gap: 10rem;

        img {
            height: 550px;
        }

        .main-text {
            width: 35rem;
            text-align: justify;

            .studies {
                margin-top: 10rem;

                li {
                    text-align: justify;
                    display: flex;

                    span {
                        color: rgba(0,0,0, .5);
                        width: 8rem;
                    }
                }
            }

            .skills {
                margin-top: 5rem;
                display: flex;
                gap: 7rem;
            }
        }
    }

    .bottom-container {
        margin-top: 7rem;

        ul {
            display: grid;
            
            li {
                margin-bottom: 5rem;
                display: flex;
                gap: 5rem;
                justify-content: center;

                .dates {
                    text-align: left;
                    color: rgba(0,0,0, .5);
                }

                .place {
                    text-align: left;
                    width: 18rem;

                    .title {
                        font-weight: 600;
                    }
                }

                .knowledges {
                    text-align: left;
                    width: 30rem;
                }
            }
        }
    }
}
</style>