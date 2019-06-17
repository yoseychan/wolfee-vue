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
            <v-btn flat color="#5d4383" @click="something(item)">Add to cart</v-btn>
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
            <v-icon @click="move()" class="btn" large color="#dcc7c6">pets</v-icon>
        </div>
        <div class="cartList magic" >
            <div class="list" v-for="(item,k) in cart" :key="k">    
              <div class="uno">{{ item.title }}</div>
              <div class="dos">{{ item.price }}</div>
              <div class="tres" @click="remove(k) ">x</div>             
            </div>
            <div class="total" v-bind="total">Total: {{ total }} &euro;</div>
            <v-btn id="checky" class="total displayNo " dark color="#241f2b">Checkout</v-btn>
        </div>
    </div>
  </v-container>

</template>

<style lang="scss">

h2{
  color: #241f2b;
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

// CART SLIDER
.cart {
    
    min-height: 400px;
    width: 300px;
    position: absolute;
    right:0;
    top: 100px;
}
.magic {
    display: inline-block;
}
.paw {
    border: 5px solid #251f2b;
    border-radius: 50%;
    width: 47px;
    height: 47px;
    background-color:#241f2b;
    position: absolute;
    left: -15px;
    top: -15px;
}

.cartOpen {
    transform: translate(250px);
    transition: .5s;
    position:fixed;
}
.cartClose {
    transform: translate(0);
    background-color: rgba(68, 58, 66, .9);
    transition: .5s;
    border-radius: 5px;
    position:fixed;
}
.cartList {
  margin: 0 0 0 50px;
  min-height:350px;
}
.list > * {
    display: inline-block;
    color: #dcc7c6;
    text-align: center;
    padding: 15px;
}
.uno {
  width: 65%;
  text-align: left;
}
.dos {
  width: 25%;
}
.tres{
  width: auto;
  padding: 5px;
  cursor: pointer;
  font-size: 18px;
}
.total {
  color: #dcc7c6;
  font-size: 20px;
  font-weight: 700;
  margin: 0 0 0 50px;

}
//cart button
#checky {
  font-weight: normal;
  font-size: 14px; 
}
.displayNo {
  display: none;
}
.displayYe {
  display: inline-block;
};

</style>


<script>
import axios from 'axios'
export default {
    data(){
        return {
            show: false,
            image: "https://cdn.pixabay.com/photo/2016/01/25/10/47/smiling-1160445_960_720.jpg",    
            urlApi: "https://api.myjson.com/bins/wlbil",
            cart: [],
            products: {},
            total: 0  
        }
    },
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
        something: function(item){
          
          this.total+= Number(item.price);
          this.cart.push({title: item.title, price: item.price});
          
          if (this.cart == "") {
          document.getElementById('checky').classList.add('displayNo');
          document.getElementById('checky').classList.remove('displayYe');
          }
          if (this.cart != "") {
          document.getElementById('checky').classList.add('displayYe');
          document.getElementById('checky').classList.remove('displayNo');
          }

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
        },

        remove: function (k){
          this.total -= Number(this.cart[k].price);
          this.cart.splice(k, 1);       
           
        },
    }

}
</script>
