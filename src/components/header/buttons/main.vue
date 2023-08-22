<template>
    <div class="header-button" @click="handleAction">
        <div v-if="text === 'cv'" class="cv-button header-button__item">
            <span class="button-text" :class="isActive">{{ text }}</span>
            <div class="icon" :class="isActive">
                <svg width="24" height="28" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M5.83398 5.83331L14.1673 14.1666" stroke="black" stroke-linejoin="round"/>
                    <path d="M14.1673 5.83331V14.1666H5.83398" stroke="black" stroke-linecap="square" stroke-linejoin="round"/>
                </svg>
            </div>
        </div>
        <div v-else class="contact-button header-button__item">
            <a href="mailto:name@rapidtables.com?subject=The%20subject%20of%20the%20mail">
                <span class="button-text">{{ text }}</span>
                <div class="icon">
                    <svg width="24" height="28" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M5.83398 5.83331L14.1673 14.1666" stroke="black" stroke-linejoin="round"/>
                        <path d="M14.1673 5.83331V14.1666H5.83398" stroke="black" stroke-linecap="square" stroke-linejoin="round"/>
                    </svg>
                </div>
            </a>
        </div>
    </div>
</template>

<script>

export default {
    
        name: 'HeaderButtons',

        props: {
            text: {
                type: String,
                default() {
                    return "";
                }
            },

            action: {
                type: String,
                default() {
                    return "";
                }
            },

            selectedCv: {
                type: Boolean,
                default: false
            }
        },
        
        data() {
            return {
                active: false
            }
        },

        methods: {
            handleAction() {
                if(this.text === 'cv') {
                    this.active = !this.selectedCv;
                }

                this.$emit(this.action, this.active);
            }
        },

        computed: {
            isActive() {
                if (this.selectedCv) {
                    return 'active';
                }

                return '';            
            }
        }
    }
</script>

<style lang="less">
.header-button, .cv-button, .contact-button a {
    margin-right: 20px;
    display: flex;
    flex-direction: row;
    height: 24px;
    color: #2c3e50;

    .button-text {
        cursor: pointer;
        text-transform: uppercase;
    }

    .icon {
        cursor: pointer;
        transition: transform .2s;
    }

    .icon.active {
        transform: rotate(180deg);
    }

    
    .button-text.active {
        font-weight: bold;
    }

    .header-button__item:hover {

        .icon {
            transform: rotate(180deg);
        }

        .button-text {
            font-weight: bold;
        }
    }
}
</style>