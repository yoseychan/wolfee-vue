<template>
    <header>
        <v-container>
           <v-layout class="align-center justify-space-between">
                <div>
                    <router-link class ="wolfee" to="/">Wolfee</router-link>
                </div>
                <div>
                    <router-link class="nav" to="/shop" >Shop</router-link>
                    <router-link class="nav" to="/about">About</router-link>
                    <router-link class="nav" to="/contact">Contact</router-link>
                </div>
                <div class="account">
                    <router-link class="nav" to="/account"><i class="fas fa-user"></i></router-link>
                </div>
            </v-layout>
        </v-container>
    </header>
</template>

<style lang="scss">
header {
    width: 100%;
    background-color: rgb(36, 31, 43);
    // position: fixed;
    div{
        text-transform: uppercase;
        .nav {
            text-decoration: none;
            color: rgb(220, 199, 198);
            font-family: 'Comfortaa', cursive;
            padding: 0 10px;
            
            
        }
        .fas {
            font-size: 24px;
        }
        .wolfee {
            text-decoration: none;
            font-size: 40px;
            color: rgb(220, 199, 198);
            font-family: 'Fredericka the Great', cursive;
            text-transform: capitalize;
        }
    }
}
.account {
    width:124px;
    
}
.container {
    padding:0;
}


</style>


<script>
export default {
    
}
</script>


