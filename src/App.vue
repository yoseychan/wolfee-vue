<template>
  <v-app>
    <v-content>
      <Header/>
    </v-content>
    <v-content>
      <Footer/>
    </v-content>
  </v-app>
</template>

<script>

import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    Footer
  },
  data () {
    return {
      //
    }
  }
}
</script>
