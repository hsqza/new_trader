<template>
  <div class="row">
    <Stock v-for="stock in stocks" :stock="stock"></Stock>
  </div>
</template>

<script>

  import Stock from './Stock.vue';

  export default {
   data() {
     return {
       stocks: [
         { id: 1, name: 'Facebook', price: 304 },
         { id: 2, name: 'Twitter', price: 242 },
         { id: 3, name: 'Google', price: 361 },
         { id: 4, name: 'Apple', price: 325 }
       ]
     }
   },
   components: {
     Stock
   }
  }
</script>
