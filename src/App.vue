<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <table width="100%">
      <tr>
        <td><Users msg="Welcome to Your Vue.js App"/></td>
        <td style="align: top"><User user="2"></User></td>
      </tr>
    </table>
  </div>
</template>

<script>
import Users from './components/Users.vue'
import User from './components/User.vue'

export default {
  name: 'App',
  components: {
    Users,
    User
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
