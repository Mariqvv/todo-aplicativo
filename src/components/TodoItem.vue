<template>
  <div class="todo-item">
    <input type="checkbox" v-model="completed" @change="toggleCompletion" />
    <span :class="{ completed: completed }">{{ task.text }}</span>
    <button @click="removeTask" class="btn btn-danger btn-sm">Remover</button>
  </div>
</template>

<script>
export default {
  props: {
    task: Object,
  },
  data() {
    return {
      completed: this.task.completed,
    };
  },
  methods: {
    toggleCompletion() {
      this.$emit("toggle", this.task.id, this.completed);
    },
    removeTask() {
      this.$emit("remove", this.task.id);
    },
  },
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>
