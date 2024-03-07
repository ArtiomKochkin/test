<template>
    <div class="button__wrap button__wrap--help">
        <button class="help button button--icon" type="button"  @click="toggleModal"></button>
        <div v-if="showModal" class="modal">
            <button class="close" @click="closeModal">&times;</button>
            
        </div>
    </div>
</template>

<script>
    export default {
        name: "TestHelp",
        data() {
            return {
                showModal: false,
            };
        },
        methods: {
            toggleModal() {
            this.showModal = !this.showModal;
        },
        closeModal() {
            this.showModal = false;
        },
    },
    }
</script>

<style scoped>
    .button__wrap {
        position: relative;
    }

    .button__wrap--help {
        grid-area: test_help;
    }

    .help {
        background: url("../assets/img/bulb.png") center no-repeat;
        background-size: cover;
        position: absolute;
        right: 0;
        top: 0;
    }

    .modal {
        position: fixed;
        top: 50%;
        left: 50%;
        width: 80%;
        height: 54%;
        transform: translate(-50%, -50%);
        background-color: rgba(189, 182, 187, 0.8);
        padding: 20px;
        border: 1px solid #ccc;
        box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        z-index: 1000;
        border-radius: 10px;
    }

    .close {
        position: absolute;
        top: 10px;
        right: 10px;
        cursor: pointer;
        background: url("../assets/img/close_btn.png") center no-repeat;
        background-size: cover;
        border: none;
        outline: none;
        padding: 0;
        width: 30px;
        height: 30px;
    }
</style>