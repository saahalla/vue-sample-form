<template>
  <v-app>
    <Navbar />
    <!-- <v-main> -->
      <v-subheader>Sample Form Dashboard</v-subheader>
      <router-view></router-view>
    <!-- </v-main> -->
    <Footer />
  </v-app>
</template>

<script>
  import Navbar from '../components/Navbar.vue'
  import Footer from '../components/Footer.vue'

  export default {
    name: 'Dashboard',

    components: {
      Navbar,
      Footer,
    },
  }
</script>
