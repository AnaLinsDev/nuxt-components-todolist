<template>
  <div class="todolist">

    <h1>Todo List</h1>
    <p> Aprendendo comunicação entre components, sem o uso de Vuex</p>

    <todo-progress 
    :progress='progress'/>

    <todo-input 
    @addTask="addTask"/>

    <todo-card-list 
    @deleteTask="deleteTask"
    @updateTask="updateTask"
    :list='list'/>

    <p v-if="list.length == 0"> Sua a vida está em dia ! </p>

  </div>
</template>

<script>
import TodoCardList from '../components/todo-card-list.vue'
import TodoInput from '../components/todo-input.vue'
import todoProgress from '../components/todo-progress.vue'

export default {

 components: { todoProgress, TodoCardList, TodoInput },

 data(){
   return {
     list : [],
     progress: 0
   }
 },

 methods:{

   addTask(title){
     if (!(title == "" || this.list.find(e => e.title == title)) ){
        this.list.unshift({title: title, status: false})
        this.setProgressBar
     }
   },

   deleteTask(index){
     this.list.splice(index, 1)
     this.setProgressBar
   },

   updateTask({status, index}){
     if (this.list[index] != undefined){
      this.list[index].status = !status
     }
     this.setProgressBar
   },

 },

 computed:{
   setProgressBar(){
     let length = this.list.length
     if(length == 0){
       this.progress = 0
       return
     }
     let done = this.list.filter(t => t.status == 1).length
     let donePercentage = (done * 100) / length
     this.progress = Math.round(donePercentage, 2)
   }
  }
}
</script>

<style >

body{ 
  background-image: linear-gradient(to bottom right, whitesmoke, rgb(49, 255, 152));
  background-attachment: fixed;
  background-size: cover;
  font-family: 'Comfortaa', cursive;
}

.todolist{
  text-align: center;
  font-size: 30px;
  margin: 50px auto;
  background-color: white;
  border: 2px solid rgb(49, 255, 152);
  width: 70vw;
  padding: 30px;
}

.todolist h1{
  margin: 0;
}

</style>