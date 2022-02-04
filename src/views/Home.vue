<template>
  <div class="home">
    <div>
      <div @click="toggleTaskForm">
        <span class="fas fa-plus-circle pointer"></span>
      </div>
      <div v-show="showTaskForm">
        <task-form/>
      </div>
    </div>
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <task-list/>
  </div>
</template>

<script>
// @ is an alias for /src
import TaskList from '@/components/TaskList.vue'
import TaskForm from '../components/TaskForm.vue'
import { bus } from '../main'

export default {
  name: 'Home',
  components: {
    TaskList,
    TaskForm
  },
  data () {
    return { showTaskForm: false }
  },
  methods: {
    // toggles form visibility
    toggleTaskForm () {
      this.showTaskForm = !this.showTaskForm
    }
  },
  created () {
    // closes the input form after new task registration
    bus.$on('addTask', (task) => {
      this.showTaskForm = false
    })
  }
}
</script>
