<template>
  <div class="list-grid">
      <div 
      v-for="(task, id) in list"
      :key="id"
      class="list-card"
      :class="{done: task.status}"
      v-on:click="updateTask( task.status, id)"
      >
      <!-- 
      Na apróxima fez, coloque uma segunda div para o card 
      e o botão fora da div, para que ele renderize n vezes,
      mas não fique dentro no card 
      -->
       <p 
       class="delete-btn" >
        <button
        v-on:click="deleteTask(id)"
        >X</button>
       </p>

       <p>{{task.title}}</p> 
       </div>
    </div>
</template>

<script>
export default {
  props:{
    list : { type: Array, required: true}
  },
 methods:{

   deleteTask(index){
     this.$emit('deleteTask', index)
   },

   updateTask(status, index){
     this.$emit('updateTask',{status, index})
   }
 }
}
</script>

<style scoped>

.list-card{
  width: 250px;
  height: 150px;
  border-radius: 10px;
  background-color: rgb(226, 78, 78);
  margin: auto;
  text-align: center;

}
.list-card p{
  margin: 0;
}

.list-grid{
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(3, 1fr);
}

.delete-btn{
  margin: 0;
  text-align: right;
}

.delete-btn button{
  width: 30px;
  height: 30px;
  font-size: 20px;
  background-color: red;
  color: wheat;
  text-align: center;
  padding: 0;
  margin: 10px;
  border-radius: 40px;
  border: 2px solid black;
}

.done{
  background-color: rgb(89, 214, 89);
  text-decoration: line-through;
}
</style>