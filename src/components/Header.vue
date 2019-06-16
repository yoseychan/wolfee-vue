<template>
    <header>
        <v-container>
           <v-layout class="align-center justify-space-between">
                <div class="account">
                    <router-link class ="wolfee" to="/">Wolfee</router-link>
                </div>
                <div>
                    <router-link class="nav" to="/shop" >Shop</router-link>
                    <router-link class="nav" to="/about">About</router-link>
                    <router-link class="nav" to="/contact">Contact</router-link>
                </div>
                <div class="account">
                    <v-badge
                        color="#dcc7c6"
                    >
                        <template v-slot:badge>
                            <span>0</span>
                        </template>
                        <v-icon class="btn" medium color="#dcc7c6">pets</v-icon>
                    </v-badge>
                </div>
            </v-layout>
        </v-container>
    </header>
</template>

<style lang="scss">
header {
    width: 100%;
    background-color: #241f2b;
    div{
        text-transform: uppercase;
        .nav {
            text-decoration: none;
            color: rgb(220, 199, 198);
            font-family: 'Comfortaa', cursive;
            padding: 0 10px;     
        }
        .wolfee {
            text-decoration: none;
            font-size: 40px;
            color: #dcc7c6;
            font-family: 'Fredericka the Great', cursive;
            text-transform: capitalize;
        }
    }
}
.account {
    width: 125px;
    
}
.container {
    padding:0;
}
.btn {
    cursor: pointer;
}


</style>


<script>
export default {
    
}
</script>


