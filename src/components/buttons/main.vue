<template>
    <div class="header-button" @click="handleAction">
        <span class="button-text" :class="isActive">{{ text }}</span>
        <div class="icon" :class="isActive">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M5.83398 5.83331L14.1673 14.1666" stroke="black" stroke-linejoin="round"/>
                <path d="M14.1673 5.83331V14.1666H5.83398" stroke="black" stroke-linecap="square" stroke-linejoin="round"/>
            </svg>
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
            }
        },
        
        data() {
            return {
                active: false
            }
        },

        methods: {
            handleAction() {
                this.$emit(this.action);
                this.active = !this.active;
            }
        },

        computed: {
            isActive() {
                if (this.active) {
                    return 'active';
                }

                return '';            
            }
        }
    }
</script>

<style lang="less">
.header-button {
    margin-right: 20px;
    display: flex;
    flex-direction: row;
    height: 1rem;

    .button-text {
        cursor: pointer;
        text-transform: uppercase;
    }

    .icon {
        cursor: pointer;
        transition: transform .3s;
    }

    .icon.active {
        transform: rotate(180deg);
    }

    .icon:hover {
        transform: rotate(180deg);
    }

    .button-text.active {
        font-weight: bold;
    }

    .button-text:hover {
        font-weight: bold;

        ~ .icon {
            transform: rotate(180deg);
        }
    } 
}
</style>