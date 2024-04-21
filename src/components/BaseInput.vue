<template>
    <div class="input_wrapper">
        <label>
            {{ label }}
            <span v-if="optional"> (Optional) </span>
        </label>
        <input
            :class="{ error, password: type === 'password' }"
            :type="inputType"
            :placeholder="placeholder"
            :value="modelValue"
            :disabled="disabled"
            @input="$emit('update:modelValue', $event.target.value)"
        />
        <img
            v-if="type === 'password'"
            class="eye"
            src="@/assets/icons/eye.svg"
            alt="Security Icon"
            @click="onChangeInputType"
        />
        <span class="flex-start-center" v-if="error && errorMessage">
            <img src="@/assets/icons/attention.png" alt="Attention" />
            {{ errorMessage }}
        </span>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
    type: {
        type: String,
        default: 'text',
    },
    label: {
        type: String,
        default: '',
    },
    placeholder: {
        type: String,
        default: '',
    },
    modelValue: {
        type: String,
        required: true,
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

const inputType = ref(props.type);

const onChangeInputType = () => {
    inputType.value = inputType.value === 'text' ? 'password' : 'text';
};
</script>

<style lang="scss" scoped>
@import '@/styles/variables/variables.scss';

.input_wrapper {
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
    input {
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
        &.password {
            padding-right: $space-32;
        }
    }

    .eye {
        position: absolute;
        top: $space-28;
        right: $space-12;
        cursor: pointer;
        width: 24px;
        height: 24px;
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
