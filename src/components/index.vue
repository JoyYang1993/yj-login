<template>
  <!--模板-->
  <div>
    <h1>Hello This is Index page!</h1>
    <button type="button" v-on:click="getIndexData">GetIndexData</button>
    <button type="button" v-on:click="logout">Log Out</button>
  </div>

</template>

<script>
  /*js*/
  export default {
    name: 'index',
    methods: {
      getIndexData: function () {
        let that = this;
        let token = sessionStorage.getItem('token');
        if(token){
          that.$http.get('http://127.0.0.1:5000/index', {
            // 将token放在请求头中发送给后台
            headers: {
              'token': token
            }
          }).then(function (response) {
            console.log(response.data)
            // token 有没有失效
            if(parseInt(response.data.code) === 200){

            }else{
              // 失效

            }
          }).catch(function (error) {
            console.log(error)
          })
        }else{
          // 如果sessionStorage中没有token,则跳转到登录页
          that.$router.push('login')
        }
      },
      logout: function () {
        sessionStorage.removeItem('token');
        this.$router.push('login')
      }
    }

  }

</script>

<style>
  /*样式*/

</style>

