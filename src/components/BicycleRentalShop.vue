<template>
  <div>
    <h1>Bicycle Rental Shop</h1>
    <p>Number of bicycles: {{ number }}</p>
    <h3>Total income({{ number}} * {{ price }}): {{ subTotal }} $</h3>
  </div>
</template>

<script>
export default {
  name: 'BicycleRentalShop',
  data () {
    return {
      number: 20,
      price: 100,
    }
  },
  computed: {
    subTotal: function () {
      return this.number * this.price;
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1:after {
    content: '🚲';
    font-weight: normal;
  }
</style>
