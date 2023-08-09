<template>
  <div id="app">
    <router-view></router-view>
    <!-- <login/> -->
  </div>
</template>

<script>
// import login from './views/Login.vue'
export default {
  name: 'App',
  // components: {
  //  login
  // },
  created() {
    this.$router.push('/login');
},
};

</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  margin-top: 20px;
}
</style>
