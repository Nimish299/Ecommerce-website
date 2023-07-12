<template>
    <div class="card h-100 w-100">
      <div class="embed-responsive embed-responsive-16by9">
        
      </div>
      
      <div class="card-body">
        <router-link :to="{ name: 'ShowDetails', params: { id: user.id } }"
          ><h5 class="card-title">{{ user.role }}</h5></router-link
        >
      
        <p class="card-text"><sup>$</sup>{{ user.email }}</p>
        <p class="card-text font-italic">
          {{ product.description.substring(0, 65) }}...
        </p>
         <router-link
          id="edit-product"
          :to="{ name: 'EditProduct', params: { id: user.id } }"
          v-show="$route.name == 'AdminProduct'"
        >
          Edit
        </router-link>
      </div> 
     
   </div>
  </template>
  
  <script>
  export default {
    name: "Customerbox",
    props: ["customer"],
    methods: {
      showDetails() 
      {
        this.$router.push({
          name: "ShowDetails",
          params: { id: this.user.id },
        });
      },
    },
  };
  </script>
  
  <style scoped>
  .embed-responsive .card-img-top {
    object-fit: cover;
  }
  
  a {
    text-decoration: none;
  }
  
  .card-title {
    color: #484848;
    font-size: 1.1rem;
    font-weight: 400;
  }
  
  .card-title:hover {
    font-weight: bold;
  }
  
  .card-text {
    font-size: 0.9rem;
  }
  
  #edit-product {
    float: right;
  }
  </style>
  