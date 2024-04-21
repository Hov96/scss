<template>
    <button :disabled="props.disabled" :class="{ 'loading flex-center-start': loading }">
        <BaseLoading small v-if="loading" />
        <span v-else>{{ label }}</span>
    </button>
</template>

<script setup>
import BaseLoading from '@/components/BaseLoading.vue';

const props = defineProps({
    label: {
        type: String,
        default: 'Click me',
    },
    disabled: {
        type: Boolean,
        default: false,
    },
    loading: {
        type: Boolean,
        default: false,
    },
});
</script>

<style lang="scss" scoped>
@import '@/styles/variables/variables.scss';

button {
    background-color: $primary-700;
    border: $border-primary-700;
    color: white;
    font-size: $fz-14;
    font-weight: 500;
    border-radius: $radius-md;
    outline: none;
    padding: $space-8 $space-10;
    cursor: pointer;
    &:hover {
        background-color: $primary-800;
    }
    &:disabled {
        background-color: $primary-700;
        cursor: not-allowed;
        opacity: 0.5;
    }

    &.loading {
        max-height: 34px;
    }
}
</style>
