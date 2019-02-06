<template>
    <transition name="fade">
        <slot></slot>
    </transition>
</template>

<script>
    export default {
        name: 'FadeAnimation'
    }
</script>

<style lang='scss' scoped>
    .fade-enter, .fade-leave-to{
        // 设置透明度 
        opacity: 0;
    }
    .fade-enter-active, .fade-leave-active{
        transition: opacity 0.5s;
    }
</style>