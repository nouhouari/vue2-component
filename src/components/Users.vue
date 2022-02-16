<template>
  <div>
    <div v-for="(user, index) in users" class="vueUser" :key="index">
      <p><img v-bind:src="user.avatar" class="avatar" /></p>
      <p>
        <strong>{{ user.first_name }}</strong>
      </p>
      <p>{{ user.last_name }}</p>
      <p>
        <a v-bind:href="'mailto:' + user.email">{{ user.email }}</a>
      </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'UsersComponent',
  data: function() {
    return {
      users: []
    }
  },
  mounted() {
    axios
      .get("https://reqres.in/api/users")
      .then((response) => (this.users = response.data.data));
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.vueUser{
        border: 1px solid #eeeeee;
        border-radius: 10px;
        text-align: center;
        margin-bottom: 5px;
        width: 100%;
        font-family: Arial;
        color: gray;
    }
    .avatar{
       border-radius: 50%; 
       border: 7px #42b883 solid;
       padding: 7px;
       background: #35495e;
    }
</style>
