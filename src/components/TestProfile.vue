<template>
    <div class="profile">
        <div class="profile__name">{{ name }}</div>
        <div class="profile__coins coins">{{ coins }}</div>
    </div>
</template>

<script>
    export default {
        name: "TestProfile",
        props: {
            name: String,
            coins: String
        }
    }
</script>

<style scoped>
    .profile {
        text-align: right;
        font-weight: 600;
        margin-top: 10vh;
    }

    .profile__name {
        padding-right: 30px;
    }

    .profile__coins {
        background: url("../assets/img/coin.png") 100% 40% no-repeat;
        background-size: 20px;
        padding-right: 30px;
        padding-top: 3px;
        font-weight: 700;
    }

    @media screen and (max-width: 991px) {
        .profile {
            margin-top: 5vh;
        }
    }
</style>