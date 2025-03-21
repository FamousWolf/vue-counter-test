<template>
  <div class="col">
    <div class="input-group mt-2 mb-2" :title="staticName">
      <span class="input-group-text w-25">
          <span class="d-inline-block text-truncate">
              {{staticName}}
          </span>
      </span>
      <span class="form-control">{{count}}</span>
      <button @click="subtractOne" class="btn btn-outline-primary">
        -<span class="d-none d-md-inline">1</span>
      </button>
      <button @click="addOne" class="btn btn-outline-primary">
        +<span class="d-none d-md-inline">1</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    /**
     * Name of the counter
     * @var string
     */
    name: {
      type: String,
      default: ''
    }
  },

  data() {
    return {
      /**
       * The count
       * @var int
       */
      count: 0,

      /**
       * Name of the counter
       * @var string
       */
      staticName: ''
    };
  },

  computed: {
    /**
     * Self
     *
     * @returns CounterList
     */
    self() {
      return this;
    }
  },

  mounted() {
    // Set static counter name
    this.staticName = this.name;

    // Empty new counter name input field
    this.$parent.newCounterName = '';

    // Set focus on new counter name input field
    this.$parent.focusInput();
  },

  methods: {
    /**
     * Add one to counter
     */
    addOne() {
      this.count++;
    },

    /**
     * Subtract one from counter
     */
    subtractOne() {
      this.count--;
    }
  }
}
</script>
