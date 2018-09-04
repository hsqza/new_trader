<template>
  <div class="col-sm-6 col-md-4">
    <div class="card my-3">
      <div class="card-header bg-primary">
        <h3 class="panel-title">
          {{stock.name}}: <small>(Price: {{stock.price}} | Quantity: {{stock.quantity}})</small>
        </h3>
      </div>
      <div class="card-body d-flex flex-row">
        <input type="number" class="form-control" placeholder="Quantity" v-model="quantity" :class="{danger: insufficientQuantity}">
        <button
          class="btn btn-primary"
          @click="sellStock"
          :disabled="insufficientQuantity || quantity <= 0">{{ insufficientQuantity ? 'Insufficient Quantity' : 'Buy' }}</button>
      </div>
    </div>
  </div>
</template>

<script>
  import { mapActions } from 'vuex';

  export default {
   props: ['stock'],
   data() {
     return {
       quantity: 0
     }
   },
   computed: {
       insufficientQuantity() {
         return this.quantity > this.stock.quantity;
       }
     },
   methods: {
     ...mapActions({
       placeSellOrder: 'sellStock'
     }),
     sellStock() {
       const order = {
         stockId: this.stock.id,
         stockPrice: this.stock.price,
         quantity: this.quantity
       };
       this.placeSellOrder(order);
       this.quantity = 0;
     }
   }
  }
</script>

<style lang="scss" scoped>
  .danger {
    border: 1px solid red;
  }
</style>
