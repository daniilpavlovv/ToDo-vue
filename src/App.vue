<template>
  <body>
    <div class="todo">
      <header class="todo__header">
        <h1 class="todo__header-title">ToDo list</h1>
      </header>
      <main class="todo__main">
        <Field @onAddTask="onAddTask" />
        <div class="todo__tasks">
          <Task
            v-for="(task, index) in tasks"
            :key="index"
            :index="index"
            :text="task.text"
            :completed="task.completed"
            @onToggleCompleted="onToggleCompleted"
            @onRemoveTask="onRemoveTask"
          />
        </div>
      </main>
    </div>
  </body>
</template>

<script>
import Field from './components/Field.vue'
import Task from './components/Task.vue'

export default {
  name: 'App',
  data: () => ({
    tasks: [],
  }),
  components: {
    Field,
    Task,
  },
  methods: {
    onToggleCompleted(index) {
      this.tasks[index].completed = !this.tasks[index].completed
    },
    onAddTask(text) {
      this.tasks.unshift({ text, completed: false })
    },
    onRemoveTask(index) {
      this.tasks.splice(index, 1)
    },
  },
}
</script>

<style>
@import './assets/css/main.css';
</style>
