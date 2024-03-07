<template>
    <div class="button__wrap button__wrap--close">
        <button class="close button button--icon" type="button"></button>
    </div>
</template>

<script>
    export default {
        name: "TestClose",
    }
</script>

<style scoped>

    .button__wrap--close {
        grid-area: test_close;
    }
    .close {
        background: url("../assets/img/close_btn.png") center no-repeat;
        background-size: cover;
    }
</style>