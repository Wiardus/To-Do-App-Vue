<template>
   <div id="input">
   <form>
     <input placeholder="Wat moet er gedaan worden..." type="text" v-model="currentTask.name">
     <button type="button" v-on:click="addTask" v-on:keyup.enter="addTask">+</button> 

   </form>

   <ol id='list'>   
      <li v-for="task in taskList" :key="task.id">
      <span :class="task.completed ? 'completed': ''"><strong>Taak: </strong>{{ task.name }}</span>
       <input type="checkbox" v-model="task.completed">
       <button type="button" v-on:click="deleteTask(taskList)">X</button> <br>
       
        
      </li>
    </ol>     
   </div> 

</template>

<script>
    export default {
        name: 'AddTask',
        data: function() {
            return {
                  id: 1,
                  taskList: [],
                  currentTask: {
                      completed: false,
                      name: '',
                      id:this.id,                      
                  }                  
               }                            
            },
             methods: {
                   addTask: function () {
                       let newTask = {
                           completed:this.currentTask.completed,
                           name:this.currentTask.name,
                           id:this.currentTask.id
                       }
                        if (this.currentTask.name.trim().length == 0) {
                            alert('Luilak!')
                            return
                        }
                       
                       this.taskList.push(newTask);
                       this.id++;
                       
                      
                     },   
                     completeTask: function () {
                         if(this.task.completed==true) {
                             this.task.setAttribute("class", "completed")
                         }
                     },
                     deleteTask: function () {
                         this.taskList.splice(this.taskList, 1)
                     },
        },
        watch: {
            taskList: {
                handler() {
                    localStorage.setItem('taskList', JSON.stringify(this.taskList))
                },
                deep: true
            }
        },
        mounted() {
            if (localStorage.getItem('taskList')) {
                this.taskList = JSON.parse(localStorage.getItem('taskList'))
            }
        }
        
    }

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
    input {
        width: 300px;
        height: 30px;
        background: whitesmoke;
    }

    button {
        position: absolute;
        width: 40px;
        height: 35px;
        font-size: 30px;
        background: none;
        border-style: none;
        cursor: pointer;
        border-radius: 5%;
    }

    button:hover {
        transform: scale(110%);
    }

    .completed{
        text-decoration: line-through;
    }

    ol {
        display: inline-block;
        align-items: center;
        font-family: 'Roboto';
        font-size: 1.5em;
    }
</style>