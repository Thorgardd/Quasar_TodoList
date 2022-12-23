// TEMPLATE HTML FOR TASK COMPONENT
<template>
  <q-page class="q-pa-lg">
    <div class="todo row" style="max-width: 900px">
      <h6 class="titleName">{{ task.name }}</h6>
      <p class="date">{{ task.date }}</p>
      <p class="boolFinished">{{ !task.isFinished ? "Non finie" : "Finie" }}</p>
      <q-btn class="finishedBtn" v-show="!task.isFinished" @click="finishingTask(task)">Fini</q-btn>
      <q-btn class="deleteBtn" @click="callback">Supprimer</q-btn>
    </div>
  </q-page>
</template>


// SCRIPT JS FOR TASK COMPONENT
<script>
export default {
  name: "Task",
  props: {
    task: Object,
    callback: Function
  },
  methods: {
    finishingTask(object){
      object.isFinished = true
    }
  }
}
</script>


// STYLE SCSS FOR TASK COMPONENT
<style lang="scss" scoped>
  .todo{
    background-color: $primary;
    justify-content: space-evenly;
    align-items: center;
    color: white;
  }
  .date{
    padding-top: 20px;
  }
  .boolFinished{
    padding-top: 20px;
  }
  .finishedBtn{
    background-color: green;
  }
  .deleteBtn{
    background-color: darkred;
  }
</style>
