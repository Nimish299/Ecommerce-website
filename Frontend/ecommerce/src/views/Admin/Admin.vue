<template>
  <div class="adminPanel container">



    <div class="container text-center">
      <div id="upup" class="row">
        <div class="col">

          <router-link :to="{ name: 'AdminProduct' }">
            <button type="button" id="Sign_in_page_order">Admin Products</button>
          </router-link>
        </div>
        <div class="col">

          <router-link :to="{ name: 'AdminCategory' }">
            <button type="button" id="Sign_in_page_order">Admin Categories</button>
          </router-link>
        </div>
        <div class="col">

          <router-link :to="{ name: 'user' }">
            <button type="button" id="Sign_in_page_order">Customer Info</button>
          </router-link>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  mounted() {
    if (!localStorage.getItem('token')) {
      this.$router.push({ name: 'Signin' });
    }
  }
}
</script>

<style>
.adminPanel {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.adminPanel button {
  font-size: 30px;
  width: fit-content;
  margin: 55px 0;
  
}

#Sign_in_page_order {
  border-style: solid;
  border-width: medium;
  padding: 10px;
  margin: 0px;
  color: #c9c9c8;
  border-color: #8fc14a;
  font-size: 30px;
  
  margin-top: 50%;
}

#Sign_in_page_order:hover {
  background-color: #8fc14a;
}
</style>