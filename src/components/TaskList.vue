<template>
  <div class="container">
    <div class="row" v-if="this.tasks.length > 0">
      <TaskCard v-for="(task, index) in tasks" :key="index"  @deleteTask="onDeleteTask" :task="task" :taskIndex="index"/>
    </div>
    <div v-else>
      <h1>
        Minden Done
      </h1>
    </div>
  </div>
</template>

<script>
// @ is an alias for /src
// Renders a list of taskcards
import TaskCard from '@/components/TaskCard.vue'
import { bus } from '../main'

export default {
  name: 'TaskList',
  components: {
    TaskCard
  },
  data () {
    return {
      tasks: [
        {
          taskName: 'Covid booster shot 14',
          taskDate: '2022.01.12',
          taskIsImportant: true
        },
        {
          taskName: 'Vue tanulás',
          taskDate: '2022.01.12',
          taskIsImportant: true
        },
        {
          taskName: 'Evés',
          taskDate: '2022.02.12',
          taskIsImportant: false
        },
        {
          taskName: 'Ivás',
          taskDate: '2022.02.12',
          taskIsImportant: false
        }
      ]
    }
  },
  methods: {
    onDeleteTask (taskIndex) {
      this.tasks.splice(taskIndex, 1)
    },
    getApiData () {
      // basic data fetching example
      // fetch("https://somehost.com/", {
      //   "method": 'GET',
      //   "headers": {
      //     host: 'somehost.com',
      //     key: 'apiKey'
      //     }
      //   })
      //   .then(response => {
      //     if (response.ok){
      //       return response.json()
      //     }
      //     else {
      //       alert('Server returned ' + response.status + ' : ' + response.statusText)
      //     }
      // })
      // .then(response => {
      //     this.tasks = response.body.taskList;
      // })
      // .catch(err => {
      //     console.log(err)
      // });
    }
  },
  created () {
    // registering event handler on event bus
    bus.$on('addTask', (task) => {
      this.tasks.push(task)
    })
  }
}
</script>
