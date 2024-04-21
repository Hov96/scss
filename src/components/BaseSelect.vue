<template>
    <div class="select_wrapper">
        <label :for="`select-${unique}`">
            {{ label }}
            <span v-if="optional"> (Optional) </span>
        </label>
        <select
            :id="`select-${unique}`"
            :disabled="disabled"
            :class="{ error }"
            @change="$emit('onChange', $event.target.value)"
        >
            <option
                :value="option.value"
                :selected="option.value?.toString() === value?.toString()"
                v-for="option in options"
                :key="option.value"
                :disabled="option.disabled"
            >
                {{ option.label }}
            </option>
        </select>
        <span class="flex-start-center" v-if="error && errorMessage">
            <img src="@/assets/icons/attention.png" alt="Attention" />
            {{ errorMessage }}
        </span>
    </div>
</template>

<script setup>
const props = defineProps({
    options: {
        type: Array,
        default: () => [],
    },
    label: {
        type: String,
        default: 'Default label',
    },
    value: {
        type: String,
        default: '',
    },
    optional: {
        type: Boolean,
        default: false,
    },
    disabled: {
        type: Boolean,
        default: false,
    },
    error: {
        type: Boolean,
        default: false,
    },
    errorMessage: {
        type: String,
        default: '',
    },
});
const unique = Date.now();
</script>

<style lang="scss" scoped>
@import '@/styles/variables/variables.scss';

.select_wrapper {
    width: 100%;
    label {
        display: block;
        margin-bottom: $space-4;
        font-size: $fz-12;
        font-weight: 500;
        span {
            color: $secondary;
        }
    }

    select {
        background-color: white;
        border: $border-grey-200;
        color: $blackBlue;
        outline: none;
        font-size: $fz-14;
        border-radius: $radius-md;
        display: block;
        width: 100%;
        padding: $space-12 $space-10;
        &:disabled {
            background-color: $grey-100;
        }
        &::placeholder {
            color: $grey-250;
        }
        &:focus {
            border: $border-focused;
        }
        &.error {
            border: $border-error;
            &:focus {
                border: $border-error;
            }
        }
    }

    span {
        font-size: $fz-12;
        color: $semantic;
        font-weight: 500;
        gap: $space-4;
        margin-top: $space-8;
        img {
            width: $space-12;
            height: $space-12;
        }
    }
}
</style>
