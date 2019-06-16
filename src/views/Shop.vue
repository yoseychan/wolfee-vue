<template>

  <v-container >
    <div  v-for="(product, j) in this.products.products" :key="j">
        <div row class="woof"><h2>{{ j }}</h2></div>
    <v-layout>

      <v-flex v-for="(item, i) in product" :key="i" row>
        <div >
        <v-card xs12 sm3 xl3>
          <v-img
            :src="item.image"
            height="300px"
          > 
          </v-img>
          <v-card-title primary-title>
            <div class="headline txtColor" v-bind="title">{{ item.title }}</div>
            <v-spacer></v-spacer>
            <div class="headline txtColor" v-bind="price">{{ item.price }} &euro;</div> 
          </v-card-title>

          <v-card-actions>
            <v-btn  icon @click="show = !show">
              <v-icon color="#5d4383">{{ show ? 'keyboard_arrow_down' : 'keyboard_arrow_up' }}</v-icon>
            </v-btn>
            <v-spacer></v-spacer>
            <v-btn  flat color="#5d4383">Add to cart</v-btn>
          </v-card-actions>

          <v-slide-y-transition>
            <v-card-text v-show="show" >
              <p v-bind="des">{{ item.des }}</p>
              <p v-bind="weight">Weight (kg): {{ item.weight }}</p>
              <p v-bind="material">Material: {{ item.material }}</p>
            </v-card-text>
          </v-slide-y-transition>
        </v-card>
        </div>
      </v-flex>

    </v-layout> 
    <div row class="woof"></div>
    </div>
  </v-container>

</template>

<style lang="scss">

h2{
  color:  #241f2b;
  font-family: 'Roboto', sans-serif;
  text-align: center;
  margin: 30px 0;
  font-size: 32px;
}
p{
  color:#2f2838; 
}
.txtColor {
  color:#2f2838;
}
.woof {
    margin: 10px;
}
</style>


<script>
import axios from 'axios'
export default {
    data: () => ({
        show: false,
        // image: {
        //   src: "https://cdn.pixabay.com/photo/2017/03/27/13/23/animal-2178696_960_720.jpg"
        // },
        urlApi: "https://api.myjson.com/bins/wlbil",
        products: {}
    }),
    mounted() {
        axios.get(this.urlApi)
            .then(response => {
                this.products = response.data;
        })
    }
  }
</script>