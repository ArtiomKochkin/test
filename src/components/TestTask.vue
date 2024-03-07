<template>
  <div class="task">
      <div class="task__desc">{{ task }}</div>
      <div class="task__question">{{ question }}</div>
      <div class="task__answers">
          <img class="task__img" :src="imagePath" alt="">
      </div>
  </div>
</template>

<script>
  export default {
      name: "TestTask",
      props: {
          question: String,
          task: String,
          imagePath: String
      }
  }
</script>
  

<style scoped>
    .task {
        margin: 0 auto;
        grid-area: test_task;
    }

    .task__desc {
        font-size: 20px;
        margin-bottom: 20px;
        font-weight: 500;
    }
    
    .task__question {
        font-size: 22px;
        font-weight: 600;
    }

    .task__answers {
        margin-top: 15vh;
    }



    @media screen and (max-width: 670px) {
        .task__desc {
            margin-bottom: 10px;
        }

        .task__img {
          width: 70vw;
        }
    }
</style>