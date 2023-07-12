<template>
    <div class="container">
      <div class="row">
        <div class="col-12 text-center">
          <h4 class="pt-3">Edit User</h4>
        </div>
      </div>
  
      <div class="row">
        <div class="col-3"></div>
        <div class="col-md-6 px-5 px-md-0">
          <form v-if="user">
            
            <div class="form-group">
              <label> first Name</label>
              <input type="text" class="form-control" v-model="user.firstName" required>
            </div>
            <div class="form-group">
              <label> Last Name</label>
              <input type="text" class="form-control" v-model="user.lastName" required>
            </div>
            <div class="form-group">
              <label> Email</label>
              <input type="email" class="form-control" v-model="user.wallet" required>
            </div>
            
            <button type="button" class="btn btn-primary" @click="editProduct">Submit</button>
          </form>
        </div>
        <div class="col-3"></div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data(){
      return {
        user: null
      }
    },
    props : ["baseURL", "users"],
    methods : {
      async edituser() {
        axios.post(this.baseURL+"user/update/"+this.id, this.user)
        .then(res => {
          //sending the event to parent to handle
          this.$emit("fetchData");
          this.$router.push({name : 'customer'});
          swal({
            text: "User Updated Successfully!",
            icon: "success",
            closeOnClickOutside: false,
          });
        })
        .catch(err => console.log("err", err));
      }
    },
    mounted() {
      if (!localStorage.getItem('token')) {
        this.$router.push({name : 'Signin'});
        return;
      }
      this.id = this.$route.params.id;
      this.user = this.users.find(user => user.id == this.id);
    }
  }
  </script>
  
  <style scoped>
  h4 {
    color: #8fc14a;
    font-family: "Helvetica 25 UltraLight", sans-serif;
    font-weight: 700;
  }
  
  </style>
  