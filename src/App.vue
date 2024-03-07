<template>
  <div class="test">
    <div class="test__inner">
      <TestProfile name="Anton" coins="1000"/> 
      <div class="center">
        <TestClose/>
        <TestTask 
          :task="currentTask.task" 
          :question="currentTask.question"
          :imagePath="currentTask.imagePath"
        />
        <TestHelp/>
      </div>
    </div>
    <TestButtons 
      :options="currentTask.options"
      :radioGroupName="'choise'"
      :selectedOption="selectedOption"
      @select-option="handleSelectOption"
      @check-answer="checkAnswer"
    />
  </div>
</template>

<script>
import TestButtons from './components/TestButtons.vue';
import TestClose from './components/TestClose.vue';
import TestHelp from './components/TestHelp.vue';
import TestProfile from './components/TestProfile.vue';
import TestTask from './components/TestTask.vue';
import tasksData from './assets/tasks.json';

export default {
  name: 'App',
  components: {
    TestButtons, TestClose, TestHelp, TestProfile, TestTask
  },
  data() {
    return {
      tasks: tasksData,
      currentTaskIndex: null,
      selectedOption: null
    };
  },
  computed: {
    currentTask() {
      return this.tasks[this.currentTaskIndex];
    }
  },
  methods: {
    generateRandomTask() {
      this.currentTaskIndex = Math.floor(Math.random() * this.tasks.length);
      this.selectedOption = null;
    },
    handleSelectOption(option) {
      this.selectedOption = option;
    },
    checkAnswer() {
      if (this.selectedOption === this.currentTask.correctAnswer) {
        alert("Correct answer!");
        this.generateRandomTask();
      } else {
        alert("Incorrect answer. Try again.");
      }
    },
  },
  mounted() {
    this.generateRandomTask();
  }
};
</script>


<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    height: 100vh;
  }

  .test {
    display: flex;
    flex-direction: column;
    height: 100%;
  }

  .test__inner {
    margin: 0 auto;
    max-width: 80vw;
    width: 100%;
    padding: 0 15px;
  }

  .center {
    margin-top: 8vh;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    grid-template-areas: 
    "test_close test_task  test_help";
  }


  /* button */

  .button {
    border: 1px solid #ccc;
    outline: none;
    display: block;
    background-color: #ccc;
    border-radius: 10px;
    padding: 10px;
    text-align: center;
    color: #212121;
    transition: all linear 0.3s;
    cursor: pointer;
    box-shadow: 1px 2px 5px;
    font-size: 16px;
    font-weight: 700;
  }

  .button:hover {
    background-color: transparent;
    box-shadow: 1px 2px 10px;
  }

  .button--icon {
    position: relative;
    width: 35px;
    height: 35px;
    border-radius: 4px;
  }


  @media screen and (max-width: 991px) {
    .test__inner {
      max-width: 95vw;
    }
  }

  @media screen and (max-width: 670px) {
    .center {
      margin-top: 4vh;
      grid-template-rows: auto auto;
      grid-template-columns: repeat(4, 1fr);
      grid-template-areas: 
      "test_close test_close test_help test_help"
      "test_task test_task test_task test_task";
    }
  }
</style>
