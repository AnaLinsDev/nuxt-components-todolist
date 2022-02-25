<template>
  <div class="desafio01">

      <form 
      @submit.prevent='submit'
      class="painel" 
      v-if="!sended">

          <h1>Formulário</h1>
          
          <input 
          class="input" 
          type="text" 
          v-model="name"
          placeholder="Nome">
          
          <input 
          class="input" 
          type="text" 
          v-model="lastname"
          placeholder="Sobrenomme">
          
          <input 
          class="input" 
          type="email" 
          v-model="email"
          placeholder="Email">

          <div class="radio" >
            <input type="checkbox" v-model="isGuest">
            <label for="checkbox">Sou convidado</label>
          </div>

          <input v-if="!isGuest"
          class="input" 
          required
          type="password" 
          v-model="password"
          placeholder="Senha">

      <select 
      class="input" 
      v-model="grupo">
          <option 
          disabled 
          value="default">Escolhe o seu Grupo</option>
          <option 
          v-for="grupo in grupos"
          :key="grupo"
          >{{grupo}}</option>
      </select>

      <button 
      type="submit"
      class="btn-verify"  > Verificar  </button>
          
      </form >

      <form-result
      v-else
      @submit="submit"
      :name='name'
      :lastname='lastname'
      :email='email'
      :password='password'
      :grupo='grupo'
       />

  </div>

</template>

<script>
import formResult from '../components/form-result.vue'
export default {
  components: { formResult },
  
data(){
  return{
    name: '',
    lastname:'',
    email:'',
    password:'',
    grupos:['Tech Bears','The Nerd Army','Backstreet Girls'],
    grupo: 'default',
    sended : false,
    isGuest: false
  }
},
methods:{
  submit(){
    this.sended = !this.sended
  }
}
}
</script>

<style>

body{
  background-color: whitesmoke;
}
.desafio01{
  display: flex;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
.painel{
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 60vw;
  min-height: 500px;
  padding: 30px;
  border-radius: 20px;
  background-color: white;
  margin: 40px auto;
  box-shadow: 0 0 1em rgb(209, 208, 208);
}

.input{
  margin-top: 20px;
  padding: 10px;
  width: 30vw;
  font-size: 20px;
  border-radius: 5px;
  border: 1px solid black;
}

.radio input{
  width: 20px;
  height: 20px;
}

.radio{
  margin-top: 20px;
  font-size: 20px;
}

.result{
  font-size: 20px;
}

hr{
  min-width: 500px;
}

.btn-verify{
  background-color: rgb(0, 255, 106);
  border: 1px solid black;
  border-radius: 5px;
  margin: 20px auto;
  width: 200px;
  font-size: 20px;
  padding: 15px;
}

</style>