<template>
  <div class="container">
    <div class="row">
      <div class="col-12 text-center">
        <h4 class="pt-3">Cutomer Details</h4>

        <!-- <router-link id="add-product" :to="{name : 'AddProduct'}" v-show="$route.name=='AdminProduct'">
            <button class="btn">Add a new Product</button>
          </router-link> -->
      </div>
    </div>
    <div class="row">
      <!-- <div v-for="product of products" :key="product.id" class="col-md-6 col-xl-4 col-12 pt-3  justify-content-around d-flex">
            <ProductBox :product="product">
            </ProductBox>
            
          </div> -->

    </div>


    <div v-for="user of users" :key="user.id">


      <hr>
      <div class="container table">
        <div class="row">
          <div class="col-2 id">
            <input class="id" type="">
            {{ user.id }}

          </div>
          <div class="col-2">
            {{ user.firstName }}
          </div>
          <div class="col-2">
            {{ user.lastName }}
          </div>
          <div class="col-2">
            {{ user.email }}
          </div>
          <div class="col-2">
            {{ user.wallet }}
          </div>
          <div class="col-2">
            <button type="submit" id="button1" class="btn btn-success ">
              Edit

            </button>

          </div>


        </div>
      </div>



    </div>



  </div>
</template>
  
<script>
const axios = require("axios");
import mounted from 'vue';
import Customerbox from './Customerbox';
export default {

  name: "customer",
  components: { Customerbox },
  data() {
    return {
      baseURL: "http://localhost:8080",
      users: []

    };
  },
  methods: {
    async getUsers() {

      await axios
        .get(`${this.baseURL}/user/`)
        .then(res => this.users = res.data)
        .catch(err => console.log(err))


    }
  },

  mounted() {

    this.getUsers();
  }
};




</script>
  
<style scoped>
.id {
  width: 1%;
  background-color: #f6f7fa;
  color: black;

  padding: 0%;
  margin: 0%;
  pointer-events: none;
  text-align: center;
  background-color: #f6f4fa;
  border: 0in;
}

h4 {
  color: #8fc14a;
  font-family: "Helvetica 25 UltraLight", sans-serif;
  font-weight: 700;
}

.table {
  display: inline;
  font-family: "Helvetica 25 UltraLight", sans-serif;
}

#add-product {
  float: right;
  font-weight: 500;
}

#button1 {
  background-color: #8fc14a;
  margin-left: 33%;
}
</style>
  