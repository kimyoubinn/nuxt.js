<template>
    <button 
        class="vue-button"
        type="button"
        :style="{ 'background-color' : bgColor }">
        <slot />
    </button>
</template>

<script lang="ts" setup>
    defineProps<{
        bgColor: string
    }>()
</script>

<style lang="scss" scoped>
button {
    background-color: #363636;
    color: #fff;
    border: none;
    padding: 10px 20px;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}
</style>