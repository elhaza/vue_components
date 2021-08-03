<template>
  <table class="tasks">
        <thead>
            <tr>
                <th>Date</th>
                <th>Hours</th>
                <th>Project</th>
                <th>Assignment Type</th>
                <th>Description</th>
                <th>Client</th>
            </tr>
        </thead>
        <tbody>
            <tr :key="index" v-for="(task, index) in tasks">
              <td>{{task.date}}</td>
              <td>{{task.hours}}</td>
              <td>{{task.project}}</td>
              <td>{{task.aType}}</td>
              <td>{{task.description}}</td>
              <td>{{task.client}}</td>
          </tr>
            
        </tbody>
    </table>
</template>

<script>
//import TaskRow from './components/TaskRow.vue'

export default {
  props: {
    tasks: {
      required:true,
      type:Array
    }
  },
  name: 'TableTasks',
}
</script>


<style scoped>
  table.tasks {
      border-collapse: collapse;
      border-spacing: 0;
      width: 100%;
      border: 1px solid #ddd;
  }

  table.tasks th, table.tasks td {
      text-align: left;
      padding: 16px;
  }

  table.tasks tr:nth-child(even) {
      background-color: #f2f2f2;
  }
</style>
