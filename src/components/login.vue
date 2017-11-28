<template>
  <!--模板-->
 <!-- <h1>
    {{ message }}
  </h1>-->

  <form novalidate>
    <label for="username">Username</label>
    <input type="text" placeholder="Please Enter your Username" id="username" v-model="username">
    <br>
    <label for="password">Password</label>
    <input type="text" placeholder="Please Enter your Password" id="password" v-model="password">
    <br>
    <button type="button" v-on:click="login">Login</button>
  </form>

</template>

<script>
  /*JS*/
  export default {
    name: 'login',
    data: function () {
      return {
       /* message: 'Hello YJ,Your Very Good!',*/
        username: '',
        password: ''
      }
    },
    methods: {
        login: function () {
         /* axios.post('http://127.0.0.1:5000/login', {
            username: this.username,
            password: this.password
          }).then(function (response) {
            console.log(response)
          }).catch(function (error) {
            console.log(error.response)
          })*/
          var request = new XMLHttpRequest();
          request.open("POST", 'http://127.0.0.1:5000/login');
          request.onreadystatechange = function(){
            if(request.readyState === 4 && request.status == 200){
              console.log(request);
            }
          };
          request.setRequestHeader("Content-Type","application/json");
          request.send(JSON.stringify({"username": this.username,"password": this.password}));
        }
    }
  }

</script>

<style>
  /*样式*/


</style>
