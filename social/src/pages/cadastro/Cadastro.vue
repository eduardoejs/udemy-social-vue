<template>
  <login-template>

    <span slot="menuesquerdo">
      <img src="https://static.quizur.com/i/b/5b035c77702c13.471891555b035c775c3ff9.54480388.png" alt="social" class="responsive-img">
    </span>

    <span slot="principal">

      <h2>Cadastro</h2>
      <input type="text" placeholder="Nome" value="">
      <input type="email" placeholder="E-Mail" value="">
      <input type="password" placeholder="Senha" value="">
      <input type="password" placeholder="Confirme sua Senha" value="">
      <button type="button" class="btn waves-effect waves-light">Enviar</button>
      <router-link to="/login" class="btn orange waves-effect waves-light">Já tenho conta</router-link>

    </span>

  </login-template>
</template>

<script>
  import LoginTemplate from '@/templates/LoginTemplate'

  export default {
    name: 'Cadastro',
    data () {
      return {

      }
    },
    components:{
      LoginTemplate
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
