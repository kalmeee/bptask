<template>
  <div class="container border-form">
        <div class="form-group">
            <label for="exampleInputEmail1">Task Name</label>
            <input v-model="task.taskName" class="form-control" type="text" name="TaskName" placeholder="">
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">Due Date</label>
            <input v-model="task.taskDate" class="form-control" type="date" name="TaskDate" >
        </div>
        <div class="form-check">
            <label class="form-check-label" for="exampleCheck1">Importatnt!</label>
            <input v-model="task.taskIsImportant" type="checkbox" class="form-check-input" id="exampleCheck1">
        </div>
        <button type="submit" @click="addTask" class="btn btn-primary">Submit</button>
  </div>
</template>

<script>
import { bus } from '../main'
// allows the registratiron of new tasks
// for loose coupling purposes tihs happens through an event
export default {
  name: 'TaskForm',
  data () {
    return {
      task: {
        taskName: '',
        taskDate: '',
        taskIsImportant: true
      }
    }
  },
  methods: {
    addTask () {
      // basic input validation
      if (this.task.taskName.length > 0) {
        bus.$emit('addTask', {
          taskName: this.task.taskName,
          taskDate: this.task.taskDate,
          taskIsImportant: this.task.taskIsImportant
        })
        this.task.taskName = ''
        this.task.taskDate = ''
        this.task.taskIsImportant = false
      }
    }
  }
}
</script>
