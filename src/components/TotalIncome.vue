<template>
  <div>

    <!-- <h3>Total income:</h3> -->
    <slot name="totalTitle">Total</slot>
    <p>{{ price }} X {{ number }} = $ {{ calcTotal }}</p>
    <button @click="clearTotal">Reset All</button>

  </div>
</template>

<script>
export default {
  name: 'TotalIncome',
  props: ['number', 'price'],
  // props: {
  //   number: {
  //     required: true,
  //     type: [String, Number], // specific data type
  //     default: 0, // set default value
  //     },
  //   price: {
  //     required: true,
  //     type: [String, Number],
  //     default: 0,
  //   },
  // },
  computed: {
    calcTotal: function () {
      // return this.number * this.price;
      let total = this.number * this.price;
      return this.numberWithCommas(total);
    },
  },
  methods: {
    clearTotal: function () {
      this.$emit('update', 0);
    },

    numberWithCommas: function (num) {
      num = num.toString();
      let pattern = /(-?\d+)(\d{3})/;
      while (pattern.test(num))
          num = num.replace(pattern, "$1,$2");
      return num;
    }
  }
}
</script>
