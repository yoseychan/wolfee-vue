<template>
  <v-layout class="main">
    <div class="hero">
      <h1>Loading a short catchy slogan..</h1>
      <div class="heroBtn">
        <v-btn flat large>
          <router-link to="Shop">View products</router-link>
      </v-btn>
    </div>
  </v-layout>
</template>


<style lang="scss">
.main {
  background-color: rgb(220, 199, 198);
  background-image: url('../assets/hero.jpg');
  background-size: cover;
  background-position: top center;
  height: 960px;
  .hero {
    h1 {
      text-align: center;
      margin-top: 600px;
      color: rgb(220, 199, 198);
      font-size: 48px;
    }
  }
}
</style>


<script>


  export default {
    
  }
</script>
