<template>
  <div class="col-sm-6 col-md-4">
    <div class="card my-3">
      <div class="card-header bg-warning">
        <h3 class="panel-title">
          {{stock.name}}: <small>(Price: {{stock.price}})</small>
        </h3>
      </div>
      <div class="card-body d-flex flex-row">
        <input type="number" class="form-control" placeholder="Quantity" v-model="quantity">
        <button
          class="btn btn-success"
          @click="buyStock"
          :disabled="quantity <= 0">Buy</button>
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
   methods: {
     buyStock() {
       const order = {
         stockId: this.stock.id,
         stockPrice: this.stock.price,
         quantity: this.quantity
       }
       this.quantity = 0;
     }
   },
  }
</script>
