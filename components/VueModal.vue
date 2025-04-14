<template>
    <transition name="modal">
        <div 
            class="vue-modal"
            @click.self="$emit('close')"
            :style="{ 'background' : dimColor }"
        >
            <div class="vue-modal__wrapper">
                <div class="vue-modal__header">
                    <p><slot name="title" /></p>
                    <nuxt-lint 
                        @click="$emit('close')"
                        to="">X</nuxt-lint>
                </div>
                <div class="vue-modal__body">
                    <slot name="content" />
                </div>
            </div>
        </div>
    </transition>
</template>

<script setup lang="ts">
    defineProps<{
        dimColor: string
    }>()
</script>

<style lang="scss" scoped>
.vue-modal {
    position: fixed;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 101;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, .5);
    z-index: 99999;
    
    &__wrapper {
        position: relative;
        width: 640px;
        z-index: 9999;	
    }

    &__header {
        position: relative;
        height: 90px;
        padding: 0 30px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        border-radius: 30px 30px 0 0;
        background-color: #ffe362;

        p {
            font-size: 42px;
            font-family: 'BMJUA';
            .point {
                color: #c83030;
            }
        }
        
        a {
            position: absolute;
            // width: 30px;
            // height: 30px;
            top: 0;
            bottom: 0;
            right: 30px;
            margin: auto;
            text-indent: -9999px;
        }
    }

    &__body {
        padding: 30px;
        background-color: #fff;
        border-radius: 0 0 30px 30px;

        p {
            text-align: center;
            font-size: 22px;
            font-weight: 500;
            line-height: 30px;
        }
    }	
}

.vue-modal-enter-active, .vue-modal-leave-active {
    transition: opacity 0.5s;
    .vue-modal__wrapper {
        transition: opacity 0.5s, transform 0.5s;
    }
}

.vue-modal-leave-active {
    transition: opacity 0.5s ease;
}

.vue-modal-enter, .vue-modal-leave-to {
    opacity: 0;

    .vue-modal__wrapper {
        opacity: 0;
        transform: translateY(-30px);
    }
}
</style>