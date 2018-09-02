<template>
  <div class="container">
    <Header></Header>
    <div class="row">
      <div class="col-12">
        <router-view></router-view>
      </div>
    </div>
  </div>
</template>

<script>
  import Header from './components/Header.vue';

  export default {
    components: {
      Header
    },
    created() {
      this.$store.dispatch('initStocks');
    }
  }
</script>

<style lang="scss">
  @import '../node_modules/bootstrap/scss/bootstrap.scss';

  html {
    font-family: 'Lato', sans-serif;
    font-size: 62.5%;
  }

  body {
    padding: 30px;
  }

</style>
