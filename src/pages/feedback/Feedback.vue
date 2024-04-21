<template>
    <div class="feedback flex-col-start-center">
        <h1>Share your feedback</h1>

        <p>
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Voluptate ab quasi
            obcaecati autem eum, aliquid maxime, molestiae sunt molestias saepe.
        </p>

        <FeedbackForm />
    </div>
</template>

<script setup>
/* The Components folder inside Feedback should contain components specific
    to the Feedback page only. Global components should be located in @/components.
*/
import FeedbackForm from '@/pages/feedback/components/FeedbackForm.vue';
</script>

<style lang="scss" scoped>
@import '@/styles/variables/variables.scss';

.feedback {
    max-width: $max-w-container;
    margin: 0 auto;
    min-height: 100vh;
    padding: $space-16;
    @media only screen and (max-width: $max-screen-md) {
        padding: $space-8;
    }

    h1 {
        text-align: center;
        width: 100%;
        margin-bottom: $space-16;
        font-weight: 700;
        font-size: $fz-48;
        @media only screen and (max-width: $max-screen-md) {
            font-size: $fz-36;
        }
        @media only screen and (max-width: $max-screen-sm) {
            font-size: $fz-30;
        }
        @media only screen and (max-width: $max-screen-xs) {
            font-size: $fz-24;
        }
    }

    p {
        max-width: 70%;
        font-size: $fz-16;
        margin-bottom: $space-32;
        text-align: center;
        @media only screen and (max-width: $max-screen-md) {
            max-width: 100%;
            font-size: $fz-14;
        }
    }
}
</style>
