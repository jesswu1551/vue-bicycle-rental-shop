<template>
  <div>

    <h1>Bicycle Rental Shop</h1>
    <p>Number of bicycles: {{ number }}</p>
    <!-- <h3>Total income({{ number}} * {{ price }}): {{ subTotal }} $</h3> -->

    <div class="button-group">
      <button @click="addCount()" :disabled="number >= 20 ? true : false">＋</button>
      <div>{{ number }}</div>
      <button @click="minusCount()" :disabled="number <= 0 ? true : false">－</button>
    </div>

    <div class="info-msg">
      <p class="text-primary" v-if="number > 0">Bikes are available.</p>
      <p class="text-error" v-else>No bike is available.</p>
    </div>

    <div class="rule-section">
      <h3>Rules</h3>
      <ol>
        <li v-for="(rule, index) in rules" :key="index">{{ rule }}</li>
      </ol>
    </div>

  </div>
</template>

<script>
export default {
  name: 'BicycleRentalShop',
  data () {
    return {
      number: 20,
      price: 100,
      rules: ['💰 $100 each time.', 'Please return no later than 18:00 🕕.', 'Be safe 🙌🏻.'],
    }
  },
  computed: {
    subTotal: function () {
      return this.number * this.price;
    }
  },
  methods: {
    addCount: function () {
      this.number++;
    },
    minusCount: function () {
      this.number--;
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .text-primary { color: #0d6efd; }

  .text-error { color: #dc3545; }

  h1:after {
    content: '🚲';
    font-weight: normal;
  }

  li { margin: 4px 0; }

  .button-group {
    display: flex;
    align-items: center;
  }

  .button-group > div {
    width: 40px;
    text-align: center;
  }
</style>
