<template>
    <div class="container">
      <div class="row">
        <div class="col-12 text-center">
          <h4 class="pt-3">Our Users</h4>
          <router-link id="add-user" :to="{name : 'AddUser'}" v-show="$route.name=='AdminUser'">
            <button class="btn">Add a new User</button>
          </router-link>
        </div>
      </div>
      <div class="row">
          <div v-for="user of users" :key="user.id" class="col-md-6 col-xl-4 col-12 pt-3  justify-content-around d-flex">
            <UserBox :user="user">
            </UserBox>
          </div>
      </div>
    </div>
  </template>
  
  <script>
  import UserBox from '../../components/User/UserBox';
  export default {
    name: 'User',
    components : {UserBox},
    props : [ "baseURL" , "users" ],
    mounted(){
      if (this.$route.name=='AdminUser' && !localStorage.getItem('token')) {
        this.$router.push({name : 'Signin'});
      }
    }
  }
  </script>
  
  <style scoped>
  h4 {
    color: #8fc14a;
    font-family: "Helvetica 25 UltraLight", sans-serif;
    font-weight: 700;
  }
  
  #add-user {
    float: right;
    font-weight: 500;
  }
  </style>
  