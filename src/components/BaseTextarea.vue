<template>
    <div class="textarea_wrapper">
        <label>
            {{ label }}
            <span v-if="optional"> (Optional) </span>
        </label>
        <textarea
            :class="{ error }"
            :maxlength="TEXTAREA_MAX_LENGTH"
            :placeholder="placeholder"
            :value="modelValue"
            :disabled="disabled"
            rows="8"
            @input="$emit('update:modelValue', $event.target.value)"
        />
        <div class="flex-between-start textarea_wrapper__info">
            <p class="textarea_wrapper__info__error" v-if="error && errorMessage">
                <img src="@/assets/icons/attention.png" alt="Attention" />
                {{ errorMessage }}
            </p>
            <p v-else-if="maxChars" class="flex-end-start textarea_wrapper__info__chars">
                Remaining Characters: {{ maxChars }}
            </p>
        </div>
    </div>
</template>

<script setup>
import { TEXTAREA_MAX_LENGTH } from '@/constants/constants.js';

const props = defineProps({
    modelValue: {
        type: String,
        required: true,
    },
    label: {
        type: String,
        default: '',
    },
    placeholder: {
        type: String,
    },
    maxChars: {
        type: Number,
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
</script>

<style lang="scss" scoped>
@import '@/styles/variables/variables.scss';

.textarea_wrapper {
    width: 100%;
    position: relative;
    label {
        display: block;
        margin-bottom: $space-4;
        font-size: $fz-12;
        font-weight: 500;
        span {
            color: $secondary;
        }
    }

    textarea {
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

    &__info {
        gap: $space-4;
        margin-top: $space-8;
        &__error {
            font-size: $fz-12;
            color: $semantic;
            font-weight: 500;
            gap: $space-4;
            white-space: nowrap;
            img {
                width: $space-12;
                height: $space-12;
            }
        }
        &__chars {
            width: 100%;
            font-size: $fz-12;
            color: $secondary;
        }
    }
}
</style>
