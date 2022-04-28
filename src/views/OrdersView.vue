<template>
  <div class="main-container">
    <h1>Manage Orders:</h1>
    <DashboardComponent />
  </div>
</template>

<script>
import DashboardComponent from '../components/Dashboard.vue';

export default {
  name: 'OrdersComponent',
  components: {
    DashboardComponent,
  },
};
</script>

<style scoped>
  .main-container{
    min-height: 450px;
  }
</style>
