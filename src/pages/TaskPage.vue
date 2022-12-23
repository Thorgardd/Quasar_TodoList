<template>
  <q-page padding>
    <h3>Page des Todos</h3>
    <div class="options" style="max-width: 700px; min-height: 0px">
      <q-btn class="q-ma-lg" color="amber" @click="createTask">Ajouter une tâche</q-btn>
      <q-btn class="q-ma-lg" color="secondary" v-show="isDisplayed" @click="validateTask">Soumettre</q-btn>
      <q-btn class="q-ma-lg"  color="deep-orange" @click="cancelTask">Annuler</q-btn>
      <div v-show="isDisplayed" class="form">
        <q-input class="q-ma-lg" type="text" v-model="name" label="Tâche à réaliser" />
        <q-input class="q-ma-lg" type="date" v-model="date" />
      </div>
    </div>
    <div class="todolist">
      <div class="singleTodo" v-for="task in tasks">
        <Task :task="task" :callback="() => deleteTask(task.id)" :task-list="tasks"/>
      </div>
    </div>
  </q-page>
</template>

<script>
import Task from "components/Task.vue";

export default {
  name: 'TaskPage',
  components: {Task},
  data(){
    return{
      id: null,
      name: "",
      isDisplayed: false,
      isFinished: false,
      tasks: [],
      date: null
    }
  },
  methods: {
    createTask(){
      this.isDisplayed = true;
    },
    cancelTask(){
      this.isDisplayed = false
    },
    validateTask(){
      let task = {
        id: Math.floor(Math.random() * 100),
        name: this.name,
        date: this.date,
        isFinished: this.isFinished
      }
      this.tasks.push(task);
      this.isDisplayed = false
    },
    deleteTask(object){
      console.log(object)
      this.tasks.splice(object.id, 1)
    }
  }
}
</script>

<style scoped>

</style>
