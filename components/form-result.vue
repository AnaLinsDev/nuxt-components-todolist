<template>
  
  <div class="painel">
        <h1>Resultado: </h1>

        <div class="result">
          <p>
            <strong> Nome Completo: </strong>
            {{name}} {{lastname}}
          </p>
          <hr>
        </div>

        <div class="result">
          <p>
            <strong> Email: </strong>
            {{email}}
          </p>
          <hr>
        </div>

        <div class="result">
          <p>
            <strong> Senha: </strong>
            {{password}}
          </p>
          <hr>
        </div>

        <div class="result">
          <p>
            <strong> Grupo: </strong>
            {{grupo}}
          </p>
          <hr>
        </div>

      <button 
      class="btn-verify" 
      @click="submit" > Voltar  
      </button>

  </div>
</template>

<script>
export default {

    props:['name','lastname','email','password','grupo'],

    methods:{
      submit(){
        this.$emit('submit')
      }
    }

}
</script>

<style>

</style>