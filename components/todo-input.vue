<template>
      <input 
      class="input" 
      v-model="title"
      v-on:keyup.enter="addTask"
      type="text" 
      placeholder="Digite sua task">
</template>

<script>
export default {

  data(){
    return{
      title:''
    }
  },

 methods:{
   addTask(){
      this.$emit('addTask', this.title)
   }
   }
}
</script>

<style scoped >

input{
  text-align: center;
  width: 300px;
  height: 50px;
  font-size: 20px;
  border: 2px solid rgb(49, 255, 152);
  border-radius: 10px;
  margin-bottom: 50px;
}

</style>