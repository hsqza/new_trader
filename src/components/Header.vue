<template>

  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <router-link to="/" class="navbar-brand">Stock Trader</router-link>

    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto nav nav-pills">
        <router-link to="/portfolio" class="nav-item" activeClass="active" tag="li"><a class="nav-link">Portfolio</a></router-link>
        <router-link to="/stocks" class="nav-item" activeClass="active" tag="li"><a class="nav-link">Stocks</a></router-link>
      </ul>
      <ul class="navbar-nav ml-auto">
        <li class="nav-item" activeClass="active"><a href="#" class="nav-link" @click="endDay">End Day</a></li>
        <li class="nav-item dropdown" activeClass="active">
          <a href=""
              class="dropdown-toggle nav-link"
              data-toggle="dropdown"
              role="button"
              aria-haspopup="true"
              aria-expanded="false">
            Save & Load
            <span class="caret"></span>
          </a>
          <ul class="dropdown-menu">
            <li><a href="#">Save Data</a></li>
            <li><a href="#">Load Data</a></li>
          </ul>
        </li>
      </ul>
      <strong class="navbar-text">Funds: {{funds | currency }}</strong>
    </div>
  </nav>
</template>


<script>
  import { mapActions } from 'vuex';

  export default {
    computed: {
      funds() {
        return this.$store.getters.funds;
      }
    },
    methods: {
      ...mapActions([
        'randomizeStocks'
      ]),
      endDay() {
        this.randomizeStocks();
      }
    },
  }
</script>


<style lang="scss" scoped>
  @import '../../node_modules/bootstrap/scss/bootstrap.scss';

  .navbar {
    margin-bottom: 20px;

    .navbar-brand {
      font-size: 2.5rem;
    }

    ul {

      .nav-item {

        a {
          font-size: 1.6rem;
        }

        &.active {
          a {
            background: lightgrey;
            color: darkgrey;
          }
        }

      }
    }


  }

</style>
