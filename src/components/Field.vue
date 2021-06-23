<template>
  <div class="todo__main__add-field">
    <input
      v-model="text"
      @keyup.enter="addTask"
      class="todo__main__add-field-input"
      type="text"
      placeholder="Enter task"
    />
    <button @click="addTask" class="button button-add">
      <span class="ripple"></span>
      <svg height="24" width="24">
        <path fill="none" d="M0 0h24v24H0z" />
        <path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z" />
      </svg>
    </button>
  </div>
</template>

<script>
export default {
  name: 'Field',
  data: () => ({
    text: '',
  }),
  methods: {
    addTask() {
      if (this.text) {
        this.$emit('onAddTask', this.text)
        this.text = ''
      }
    },
  },
}
</script>

<style scoped></style>
