<template>
  <div id="app">
    <el-container class="container">
      <el-header class="header">

        <el-menu default-active="1" class="el-menu-diy" mode="horizontal">
          <el-menu-item index="0"><img src="../public/logo.png" style="height:50px;display: inline;" /></el-menu-item>

          <el-menu-item index="2" class="el-menu-item-float" v-if="user_status">{{username}}</el-menu-item>
          <el-menu-item index="1" class="el-menu-item-float" v-if="login_status">哈哈哈</el-menu-item>
          <el-menu-item index="1" class="el-menu-item-float" v-if="login_status">哈哈哈</el-menu-item>
          <!--<el-menu-item index="3" class="el-menu-item-float"></el-menu-item>-->
        </el-menu>

      </el-header>
      <el-container>
        <el-main>
          <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
  name: 'app',
  data(){
    return{
      login_status: 'hidden',
      user_status:'hidden',
      username: ''
    }
  },
  created() {
    this.getUser();
  },
  methods:{
    getUser: function(){
      const username = this.$cookies.get('username');
      const sessionKey = this.$cookies.get('sessionKey');
      const that = this;
      if(username === undefined || username == "" || sessionKey === undefined || sessionKey == ""){
        that.login_status = true;
        that.user_status = false;

      }else{
        that.login_status = false;
        that.user_status = true;
        that.username = username;
      }
    }
  }
}
</script>

<style>
  body {
    margin:0;

  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    margin:0;
    padding:0;
  }
  .header {
    padding:0 !important;
    margin:0;
  }
  .container {
    padding:0 !important;
    margin:0;
  }
  .el-menu-diy {

  }
  .el-menu-item-float {
    float: right !important;
  }
  .avatar {
    width:35px;
    height:35px;
    border-radius: 50%;
  }
  .el-container {
    height: 100vh !important;
  }
  .el-main {
    height: 100% !important;
  }
</style>
