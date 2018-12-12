<template>
  <login-template>

    <span slot="menuesquerdo">
      <img src="https://static.quizur.com/i/b/5b035c77702c13.471891555b035c775c3ff9.54480388.png" alt="social" class="responsive-img">
    </span>

    <span slot="principal">

      <h2>Login</h2>
      <input type="email" placeholder="E-Mail" value="">
      <input type="password" placeholder="Senha" value="">
      <button type="button" class="btn waves-effect waves-light">Entrar</button>
      <router-link to="/cadastro" class="btn orange waves-effect waves-light">Cadastre-se</router-link>

    </span>

  </login-template>
</template>

<script>
  import LoginTemplate from '@/templates/LoginTemplate'

  export default {
    name: 'Login',
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
