<template>
  <div id="app">
    <h1>Bicycle Rental Shop</h1>
    <p>Number of bicycles: {{ number }}</p>

    <div class="button-group">
      <button @click="addCount" :disabled="number >= 20 ? true : false">＋</button>
      <div>{{ number }}</div>
      <button @click="minusCount" :disabled="number <= 0 ? true : false">－</button>
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

    <TotalIncome :number="number" :price="price"/>
  </div>
</template>

<script>
import TotalIncome from './components/TotalIncome.vue'

export default {
  name: 'App',
  components: {
    TotalIncome,
  },
  data () {
    return {
      number: 20,
      price: 100,
      rules: ['💰 $100 each time.', 'Please return no later than 18:00 🕕.', 'Be safe 🙌🏻.'],
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

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin: auto;
  margin-top: 60px;
  width: 600px;
}

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
