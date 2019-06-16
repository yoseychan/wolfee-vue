<template>

  <v-container >
    <div  v-for="(product, j) in this.products.products" :key="j">
        <div row class="woof"><h2>{{ j }}</h2></div>
    <v-layout>

      <v-flex  v-for="(item, i) in product" :key="i" row>

        <v-card xs12 md3 xl3 >
          <v-img
            :src="image"
            height="300px"
          > 
          </v-img>
          <v-card-title primary-title>
            <div class="headline txtColor" v-bind="title">{{ item.title }}</div>
            <v-spacer></v-spacer>
            <div class="headline txtColor" v-bind="price">{{ item.price }} &euro;</div> 
          </v-card-title>

          <v-card-actions>
            <v-btn icon @click="show = !show">
              <v-icon color="#5d4383">{{ show ? 'keyboard_arrow_down' : 'keyboard_arrow_up' }}</v-icon>
            </v-btn>
            <v-spacer></v-spacer>
            <v-btn flat color="#5d4383" @click="something()">Add to cart</v-btn>
          </v-card-actions>

          <v-slide-y-transition>
            <v-card-text v-show="show" >
              <p v-bind="des">{{ item.des }}</p>
              <p v-bind="weight">Weight (kg): {{ item.weight }}</p>
              <p v-bind="material">Material: {{ item.material }}</p>
            </v-card-text>
          </v-slide-y-transition>
        </v-card>

      </v-flex>

    </v-layout> 
    <div row class="woof"></div>
    </div>


    <div class="cartOpen cart"  id="swoosh">
        <div class="paw magic">
            <v-badge
            color="#241f2b"
            >
                <template v-slot:badge>
                    <span>0</span>
                </template>
                <v-icon @click="move()" class="btn" medium color="#241f2b">pets</v-icon>
            </v-badge>
        </div>
        <div class="cartList magic">
            <div>meow</div>
        </div>
    </div>
  </v-container>

</template>

<style lang="scss">

h2{
  color:  #241f2b;
  font-family: 'Fredericka the Great', cursive;
  text-align: center;
  margin: 30px 0;
  font-size: 32px;
  text-transform: capitalize;
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
.cart {
    
    min-height: 600px;
    width: 300px;
    position: absolute;
    right:0;
    top: 100px;
}
.magic {
    display: inline-block;
}
.paw {
    margin: 0 10px 0 0;
}
.cartList{
    margin: 0 0 0 50px;
    background-color: #241f2b;
    min-height: 550px;
    width: 300px; 
}
.cartOpen {
    transform: translate(250px);
}
.cartClose {
    transform: translate(0);
}
</style>


<script>
import axios from 'axios'
export default {
    data: () => ({
        show: false,
        image: "https://cdn.pixabay.com/photo/2019/06/12/15/07/cat-4269479_960_720.jpg",    
        urlApi: "https://api.myjson.com/bins/wlbil",
        products: {}
    }),
    mounted() {
        axios.get(this.urlApi)
            .then(response => {
                this.products = response.data;
        })
        var cartOpen = agCookie.read('cart');
        if( cartOpen == null || cartOpen === "closed") {
            document.getElementById('swoosh').classList.add('cartOpen');
        } else {
            document.getElementById('swoosh').classList.add('cartClose');
        }

    },    
    methods: {
        something: function() {
            alert('hello')
        },
        move: function() {
            var cartOpen = agCookie.read('cart');
            if (cartOpen == null || cartOpen === "closed") {
                document.getElementById('swoosh').classList.add('cartClose');
                document.getElementById('swoosh').classList.remove('cartOpen');
                agCookie.create('cart', 'opened');
            }else {
                document.getElementById('swoosh').classList.add('cartOpen');
                document.getElementById('swoosh').classList.remove('cartClose');
                agCookie.create('cart', 'closed');
            }
            
        }

    }

}
</script>