<template>
   <div class="vueUser">
     <div v-if="user">
     <p><b>User details</b></p>
      #{{userid}}
      <p><img v-bind:src="user.avatar" class="avatar" /></p>
      <p>
        <strong>{{ user.first_name }}</strong>
      </p>
      <p>{{ user.last_name }}</p>
      <p>
      <a v-bind:href="'mailto:' + user.email">{{ user.email }}</a>
      </p>
     </div>
     <div v-else>
      No user selected
     </div>
     <div>
      <button v-on:click="read()">Read from local storage</button>
     </div>
 </div>
</template>

<script>
import axios from "axios";

export default {
    name: 'UserComponent',
    data: function(){
        return {
            user: null
        }
    },
    props: ['userid'],
    mounted(){
        if (this.userid){
          axios
      .get("https://reqres.in/api/users/" + this.userid)
      .then((response) => (this.user = response.data.data));
        }
    },
    updated() {
         axios
      .get("https://reqres.in/api/users/" + this.userid)
      .then((response) => (this.user = response.data.data));
    },
    methods:{
      read(){
        console.log('Read from local storage');
        alert(localStorage.DATA)
      }
    }
}
</script>

<style scoped>
.vueUser{
        border: 1px solid #eeeeee;
        border-radius: 10px;
        text-align: center;
        margin-bottom: 5px;
        width: 100%;
        font-family: Arial;
        color: gray;
        background: #fafafa;
    }
    .avatar{
       border-radius: 50%; 
       border: 7px #42b883 solid;
       padding: 7px;
       background: #35495e;
    }
</style>
