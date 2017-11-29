<template>
  <!--模板-->
  <form novalidate>
    <label for="username">用户名</label>
    <input type="text" placeholder="Please enter your username" id="username" v-model="username">
    <br>
    <label for="password">密码</label>
    <input type="password" placeholder="Please enter your password" id="password" v-model="password">
    <br>
    <button v-on:click="login" type="button">Login</button>
  </form>
</template>

<script>
  /*js*/
  export default {
    name: 'login',
    data: function () {
      return {
        username: '',
        password: ''
      }
    },
    methods: {
      login: function () {
        this.$http.post('http://127.0.0.1:5000/login', {
          username: this.username,
          password: this.password
        }).then(function (response) {
          console.log(response);
          if(parseInt(response.code) === 400){
            // 登录失败


          }else if (parseInt(response.code) === 200){
            // 登录成功

          }
        }).catch(function (error) {
          console.log(error)
        })
      }
    }
  }
</script>

<style>
  /*样式*/
</style>
