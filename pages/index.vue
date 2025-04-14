<template>
    <div>
        <h1>NUXT STUDY</h1>

        <vue-button 
            bg-color="#000"
            @click="handleOpenModal">
            CLICK ME
        </vue-button>

        <vue-modal
            v-show="isModalVisible"
            @close="handleCloseModal">
            <template #title>title area</template>
            <template #content>content area content area content area content area content area content area content area content area</template>
        </vue-modal>
    </div>
</template>

<script lang="ts" setup>
    import { ref } from 'vue';
    
    const isModalVisible = ref<boolean>(false);

    const handleCloseModal = (): void => {
        isModalVisible.value = false;
    }

    const handleOpenModal = (): void => {
        isModalVisible.value = true;
    }
</script>

