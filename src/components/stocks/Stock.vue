<template>
  <div class="col-sm-6 col-md-4">
    <div class="card my-3">
      <div class="card-header bg-success">
        <h3 class="panel-title">
          {{stock.name}}: <small>(Price: {{stock.price}})</small>
        </h3>
      </div>
      <div class="card-body d-flex flex-row">
        <input type="number" :class="['form-control', {danger: insufficientFunds}]" placeholder="Quantity" v-model="quantity">
        <button
          class="btn btn-success"
          @click="buyStock"
          :disabled="insufficientFunds || quantity <= 0">{{ insufficientFunds ? 'Insufficient Funds' : 'BUY' }}</button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
   props: ['stock'],
   data() {
     return {
       quantity: 0
     }
   },
   computed: {
     funds() {
       return this.$store.getters.funds;
     },
     insufficientFunds() {
       return this.quantity * this.stock.price > this.funds;
     }
   },
   methods: {
     buyStock() {
       const order = {
         stockId: this.stock.id,
         stockPrice: this.stock.price,
         quantity: parseInt(this.quantity)
       }

      this.$store.dispatch('buyStock', order);
      this.quantity = 0;
     }
   },
  }
</script>

<style lang="scss" scoped>
  @import '../../../node_modules/bootstrap/scss/bootstrap.scss';

  .danger {
    border: 2px solid red;
  }

</style>

