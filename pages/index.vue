<template>
  <div class="container">
    <h1 class="text-center my-5 text-warning">Multiple Counters</h1>
    <div class="row justify-content-center my-5">
      <input
        class="w-25 mx-1 border border-top-0 border-right-0 border-left-0 border-warning"
        type="number"
        v-model.number="step"
        placeholder="Step"
        step="0.1"
        autofocus
        @keyup.enter="addCounter"
      />
      <button class="mx-1 btn btn-outline-warning" @click="addCounter">
        Add counter
      </button>
    </div>
    <div class="row">
      <counter
        v-for="counter in counters"
        :key="counter.id"
        :step="counter.step"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      step: null,
      counters: []
    };
  },
  methods: {
    // addCounter first check if the input is acceptable then push it into the counter card
    addCounter() {
      if (/^[\-\+]?\d*\.?\d?$/.test(this.step)) {
        this.counters.push({
          id: this.counters.length,
          step: this.step
        });
        this.step = null;
      } else {
        alert(
          "Please enter a negative or positive integer or a float with one decimal."
        );
      }
    }
  }
};
</script>
