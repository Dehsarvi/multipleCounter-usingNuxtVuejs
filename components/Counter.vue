<template>
  <div class="card-group d-inline-block">
    <div class="card shadow m-2 bg-white rounded border-warning">
      <div class="card-body text-center">
        <h4 class="card-title text-warning">{{ innerStep }} Step</h4>
        <h1 class="card-text text-center">{{ fixedInnerValue }}</h1>
        <button
          class="btn btn-outline-warning "
          @click="run"
          @keydown.enter="run"
        >
          run!
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "counter",
  data() {
    return {
      innerStep: this.step,
      innerValue: 0
    };
  },
  props: {
    //input of step from parent index.vue
    step: Number
  },
  computed: {
    //only accept float number with one decimal digit
    fixedInnerValue() {
      // https://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html
      return this.innerValue.toFixed(1);
    }
  },
  methods: {
    run() {
      this.innerValue += this.innerStep;
    }
  }
};
</script>
