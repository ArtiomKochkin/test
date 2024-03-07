<template>
  <div class="form-wrap">
    <form class="form">
      <div v-for="(option, index) in options" :key="index" class="form__choise">
        <input
          type="radio"
          :name="radioGroupName"
          :id="'choise' + index"
          class="form__input"
          :checked="selectedOption === option"
          @change="selectOption(option)"
        />
        <label :for="'choise' + index" class="form__label">{{ option }}</label>
      </div>
      <button type="button" class="form__btn button" @click="checkAnswer">Check</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "TestButtons",
  props: {
    options: Array,
    radioGroupName: String,
    selectedOption: String,
  },
  methods: {
    selectOption(option) {
      this.$emit("select-option", option);
    },
    checkAnswer() {
      this.$emit("check-answer");
    },
  },
};
</script>

<style scoped>

    .form-wrap {
        margin: auto 0 10px 0;
        padding: 0 10px;
    }

    .form {
        display: grid;
        grid-template-columns: 27% 27% 27% 15%;
        gap: 15px;
    }

    .form__choise {
        position: relative;
    }

    .form__input {
        position: absolute;
        left: 0;
        top: -30%;
        z-index: 1;
        outline: none;
        border: 1px solid #ccc;
        background-color: #ccc;
        box-shadow: 1px 2px 5px;
        border-radius: 10px;
        cursor: pointer;
        appearance: none;
        width: 100%;
        height: 100%;
        cursor: pointer;
    }

    .form__input:hover,
    .form__input:checked {
        background-color: transparent;
        box-shadow: 1px 2px 10px;
    }

    .form__label {
        font-size: 18px;
        color: #212121;
        padding: 10px;
        font-weight: 700;
        text-align: center;
        position: relative;
        z-index: 1;
    }

    .form__btn {
        position: relative;
        top: -25%;
    }



    @media screen and (max-width: 991px) {
        .form {
            grid-template-columns: 26% 26% 26% 15%;
        }
    }

    @media screen and (max-width: 670px) {

        .form__choise--A {
            grid-area: button_A;
        }
        .form__choise--B {
            grid-area: button_B;
        }
        .form__choise--C {
            grid-area: button_C;
        }

        .form__btn {
            grid-area: button_submit;
        }

        .form {
            grid-template-columns: repeat(3, 1fr);
            grid-template-rows: 1fr 1fr;
            grid-template-areas: 
            "button_A button_B button_C"
            "button_submit button_submit button_submit";
        }
    }
</style>