<template>
  <v-layout class="main">
    <div class="hero">
      <h1>Loading a short catchy slogan..</h1>
      <div class="heroBtn">
        <v-btn class="viewProducts" light large color="#dcc7c6">
          <router-link class="view" to="Shop">View products</router-link>
        </v-btn>
      </div>
    </div>  
  </v-layout>
</template>


<style lang="scss">
.main {
  background-color: #dcc7c6;
  background-image: url('../assets/hero.jpg');
  background-size: cover;
  background-position: top center;
  height: 960px;
  .hero {
    width: 100%;
    h1 {
      text-align: center;
      margin-top: 600px;
      color: rgb(220, 199, 198);
      font-size: 48px;
      font-family: 'Fredericka the Great', cursive;
    }
  }
}
.view {
  text-decoration: none;
  color: #241f2b;
}
.heroBtn {
  width: 200px;
  height: 50px;
  margin: 0 auto
}
</style>


<script>
  export default {
    
  }
</script>
