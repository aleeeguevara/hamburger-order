<template>
  <nav id="nav">
    <router-link to="/" id="logo-url">
      <img :src="logo" :alt="alt" id="logo">
    </router-link>
    <router-link to="/">Home</router-link>
    <router-link to="/orders">Orders</router-link>
  </nav>
</template>

<script>
export default {
  name: 'NavbarComponent',
  props: ['logo', 'alt'],
};
</script>

<style scoped>
  #nav{
    background-color: #222;
    border-bottom: 4px solid #111;
    padding: 15px 50px;
    align-items: center;
    display: flex;
    justify-content: flex-end;
  }
  #logo{
    max-width: 60px;
    height: 60px;
  }
  #nav #logo-url {
    margin: auto;
    margin-left: 0;
  }

  #nav a {
    color: #FCBA03;
    text-decoration: none;
    margin: 12px;
    transition: .5s;
  }

  #nav a:hover{
    color: #fff;
  }
</style>
