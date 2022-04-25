<template>
  <NavbarComponent logo="/img/logo.png" alt='Make Your Burger'/>
  <router-view/>
  <FooterComponent />
</template>

<script>
import NavbarComponent from './components/Navbar.vue';
import FooterComponent from './components/Footer.vue';

export default {
  components: {
    NavbarComponent,
    FooterComponent,
  },

};
</script>

<style>
  *{
    font-family: Arial, Helvetica, sans-serif;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
  .main-container {
    margin: 50px;
    min-height: 250px;
  }

  h1{
    text-align: center;
    font-size: 42px;
    margin-bottom: #222;
  }
</style>
