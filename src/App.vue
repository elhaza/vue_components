<template>
  <div class="container" id="TrackerApp">
    <form class="form" v-on:submit.prevent="addTask()" method="post">
        <div>
            Date: <input class="date" v-model='date' name="txtFrom" type="date" required />
            Hours: <input class="time" v-model='hours' name="TiempoTextBox" type="number" step="any" />
        </div>
        <div>
            <select v-model='project' name="idProyectoDropDownList" required>
                <option value="">Select Project</option>
                <option v-for="project in projects" v-bind:value="project" :key="project.id">{{project.name}}</option>
            </select>
        </div>

        <div>
            <select v-model='aType' name="idAType" required>
                <option value="">Select Assignment Type</option>
                <option v-for="aType in assignmentTypes" v-bind:value="aType" :key="aType.id">{{aType.name}}</option>
            </select>
        </div>
        
        <div><textarea v-model='description' cols="20" name="DescripcionTextBox" rows="5" placeholder="Description (500 characters max)" required></textarea></div>
        <div>
            <select v-model="client" name="idFocalPointClientDropDownList" required>
                <option value="">Select Client Focal Point</option>
                <option v-for="client in clients" :key="client">{{client}}</option>
            </select>
        </div>
        <div>
            <div><input name='btnAceptar' type="submit" value="Add" /></div>
        </div>
    </form>

    <img v-bind:src="displayRole">

    <table-tasks :tasks="tasks"></table-tasks>
</div>
</template>

<script>

import TableTasks from './components/TableTasks.vue'

export default {
  name: 'App',
  components: {
    TableTasks
  },
  data(){
        return {
            date: '',
            hours: 0,
            project:'',
            aType: '',
            description: '',
            client:'',
            image: 'images/project-manager.png',
            projects: [{id:1, name:'Vue Js mentoring program'}, {id:2, name:'Arvig'}],
            assignmentTypes:[{id: 100, name: 'Vue Js trainning'}, {id: 21, name: 'Account Management'}, {id: 6, name: 'Administration'},
                {id: 31, name: 'Applicants Sourcing'}, {id: 7, name: 'Call Center'}, {id: 34, name: 'Coding Challenges Review'},
                {id: 11, name: 'Communication (newsletter, notas, etc)'}, {id: 15, name: 'Configuration Management'}, {id: 17, name: 'Data Entry'},
                {id: 14, name: 'DBA'}, {id: 30, name: 'Executive Headhunting'}, {id: 25, name: 'Facilities'}, {id: 29, name: 'Farming - Staffing Hero'},
                {id: 23, name: 'Finance'}, {id: 22, name: 'Help Desk/Support'}, {id: 45, name: 'High Performance Program'},
                {id: 27, name: 'Human Resources'}, {id: 16, name: 'Infrastructure/Hardware'}, {id: 5, name: 'Management'},
                {id: 20, name: 'Marketing'}, {id: 43, name: 'Mentoring'}, {id: 38, name: 'On Boarding &amp; Training'},
                {id: 39, name: 'On Call Duties'}, {id: 41, name: 'Presales'}, {id: 2, name: 'Recruitment'}, {id: 8, name: 'Reports Generation'},
                {id: 19, name: 'Sales'}, {id: 37, name: 'Sales Support'}, {id: 9, name: 'Sin tareas asignadas / Idle'},
                {id: 1, name: 'Software Development'}, {id: 36, name: 'Sourcing'}, {id: 44, name: 'Sourcing Weekend Shift / OT Hours'},
                {id: 24, name: 'Staffing'}, {id: 32, name: 'Technical Interviews'}, {id: 42, name: 'Technical Interviews'},
                {id: 33, name: 'Test Review'}, {id: 13, name: 'Testing'}, {id: 4, name: 'Training'}, {id: 10, name: 'UI/UX/Graphic Design'}],
            clients: ["Jonathan Chavez", "Victor Antunes"],
            tasks:[
                {date:'2021-01-01', project:"Arvig", hours: '8', aType:"Sourcing", description: 'Initial Row #01 for testing', client:"Victor Antunes"},
                {date:'2021-01-01', project:"Vue Js mentoring program", hours: '2', aType:"Vue Js trainning", description: 'Row #02 for testing purposes', client:"Jonathan Chavez"},
                {date:'2021-01-01', project:"Arvig", hours: '4', aType:"Vue Js trainning", description: 'Description goes here', client:"Jonathan Chavez"}

            ]
        }
    },
    methods: {
        addTask(){
            this.tasks.push({date:this.date, project:this.project.name, hours: this.hours, aType: this.aType.name,
                description: this.description, client:this.client});
                this.aType = '';
                this.description = '';
        }
    },
    computed: {
        displayRole(){
            if (this.client==='Jonathan Chavez'){
                return 'images/training.png';
            } else if (this.client==='Victor Antunes') {
                return 'images/project-manager.png';
            }
            return 'images/welcome.jpg'
        },
        //In 3.x, filters are removed and no longer supported in the same way that 2.x
    }
}
</script>

<style>
*{
    font-family: Arial;
}
.container {
    margin: auto;
    width: 1200px;
}
.container .form {
    border: solid 1px #d5e5ff;
    background-color: #fff;
    box-shadow: 6px -5px 5px rgb(179 173 212);
    border-radius: 25px;
    padding: 40px;
    width: 500px;
    margin: auto;
}

.container .form input, .container .form select, .container .form textarea {
    width: 500px;
    min-height: 23px;
    margin-bottom: 10px;
}

.container .form input.date {
    width: 170px;
    margin-right: 23px;
}
.container .form input.time {
    width: 50px;
 }

img {
    max-width: 130px;
}

</style>
