<template>
  <div class="todo-list">
    <h3>Lista de Tarefas</h3>
    <todo-item
      v-for="task in tasks"
      :key="task.id"
      :task="task"
      @toggle="toggleTaskCompletion"
      @remove="removeTask"
    />
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  components: {
    TodoItem,
  },
  props: {
    tasks: Array,
  },
  methods: {
    toggleTaskCompletion(id, completed) {
      this.$emit("toggle", id, completed);
    },
    removeTask(id) {
      this.$emit("remove", id);
    },
  },
};
</script>

<style scoped>
.todo-list {
  margin-top: 20px;
}
</style>
