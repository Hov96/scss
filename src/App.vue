<template>
    <div class="main">
        <nav class="flex-center-start">
            <router-link to="#">My Awesome Website</router-link>
        </nav>
        <router-view />
    </div>
</template>

<style lang="scss" scoped>
@import '@/styles/variables/variables.scss';

.main {
    width: 100%;
    color: $blackBlue;
    nav {
        border-bottom: 1px solid $blackBlue;
        padding: $space-20 $space-8;
        box-shadow: 0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1);
        user-select: none;
        background-color: $bg-navbar;
        a {
            color: white;
        }
    }
}
</style>
