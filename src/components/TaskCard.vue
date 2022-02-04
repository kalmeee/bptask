<template>
  <div class="col-md-4">
    <div :class="'card text-white m-2 ' + (this.task.taskIsImportant? 'bg-danger' : 'bg-primary')">
      <div class="card-header">
        <div @click="deleteTask">
          <span class="fa fa-trash pointer"></span>
        </div>
      </div>
      <div class="card-body">
        <h5 class="card-title">{{this.task.taskName}}</h5>
        <!-- if no deadline was added defaults to None -->
        <p class="card-text">Deadline: {{this.task.taskDate? this.task.taskDate : 'None'}}</p>
      </div>
    </div>
  </div>
</template>

<script>
// represents a task
export default {
  name: 'TaskCard',
  props: {
    task: {
      taskName: String,
      taskDate: String,
      taskIsImportant: Boolean
    },
    taskIndex: Number
  },
  methods: {
    deleteTask () {
      this.$emit('deleteTask', this.taskIndex)
      console.log('emited task index' + this.taskIndex)
    }
  }
}
</script>
