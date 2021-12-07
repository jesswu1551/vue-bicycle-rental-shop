<template>
  <div id="app">

    <h1>Bicycle Rental Shop</h1>
    <div class="section">
      <span class="icon-text">🚲 </span><h2>Bike Available</h2>
      <div class="button-group">
        <button @click="addCount" :disabled="number >= 20 ? true : false">+</button>
        <span :class="number == 0 ? 'text-error' : ''">{{ number }}</span>
        <button @click="minusCount" :disabled="number <= 0 ? true : false">-</button>
      </div>
      <div class="info-msg">
        <span class="text-error" v-if="number == 0">No bike is available.</span>
      </div>
    </div>

    <!-- <TotalIncome :price="price" :number="addIncome" @update="resetNumber"/> -->
    <TotalIncome :price="price" :number="addIncome" @update="resetNumber">
      <template #totalTitle>
        <span class="icon-text">💰 </span><h2>{{ title.total }}</h2>
      </template>
    </TotalIncome>

    <div class="section">
      <span class="icon-text">📜 </span><h2>Rules</h2>
      <ol>
        <li v-for="(rule, index) in rules" :key="index">{{ rule }}</li>
      </ol>
    </div>

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
      addIncome: 0,
      title: {
        total: 'Total Income',
      }
    }
  },
  methods: {
    addCount: function () {
      this.number += 1;
    },

    minusCount: function () {
      this.number -= 1;
      this.addIncome += 1;
    },

    resetNumber: function () {
      this.addIncome = 0;
    },
  }
}
</script>

<style>
*, *::before, *::after { box-sizing: border-box; }

#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: auto;
}

.text-primary { color: #0d6efd; }

.text-error { color: #dc3545; }

li { margin: 4px 0; }

h2 { display: inline-block; }

.icon-text { font-size: 1.5rem; }

.section {
  margin: 24px 0;
  padding: 12px 0;
}

.section ol {
  margin: auto;
  width: 350px;
  text-align: left;
}

.button-group > span {
  display: inline-block;
  width: 72px;
  font-size: 28px;
  font-weight: bold;
}

.button-group > button {
  width: 28px;
  height: 28px;
  font-size: 20px;
  background-color: #ececec;
  border-radius: 4px;
  border: none;
}

.button-group > button:hover:not(:disabled) {
  background-color: #dfdfdf;
  cursor: pointer;
}

.info-msg { margin-top: 8px; }

.total-body {
  margin-bottom: 16px;
  font-size: 28px;
  font-weight: bold;
  color: #f28629;
}

.reset-btn {
  background-color: #ececec;
  padding: 8px 16px;
  border-radius: 4px;
  border: none;
}

.reset-btn:hover:not(:disabled) {
  background-color: #dfdfdf;
  cursor: pointer;
}
</style>
