<template>
  <div id="app" class="container">
    <h1>Lista de Tarefas</h1>
    <div class="form-group">
      <input
        type="text"
        v-model="newTask"
        class="form-control"
        placeholder="Digite uma tarefa"
        @keyup.enter="addTask"
      />
    </div>
    <todo-list
      :tasks="tasks"
      @toggle="toggleTaskCompletion"
      @remove="removeTask"
    />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";

export default {
  components: {
    TodoList,
  },
  data() {
    return {
      newTask: "",
      tasks: [],
      nextId: 1,
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({
          id: this.nextId++,
          text: this.newTask,
          completed: false,
        });
        this.newTask = "";
      }
    },
    toggleTaskCompletion(id, completed) {
      const task = this.tasks.find((task) => task.id === id);
      if (task) {
        task.completed = completed;
      }
    },
    removeTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
  },
};
</script>

<style>
#app {
  margin-top: 50px;
}
</style>
