<template>
  <nav class="navbar bg-light border-bottom p-4">
    <div class="container">
      <div class="btn-toolbar w-100">
        <div class="input-group me-2 w-75">
          <input type="text" v-model="newCounterName" class="form-control form-control-lg" id="newCounterName" placeholder="Counter name" @keyup.enter="addCounter" />
          <button @click="addCounter" class="btn btn-primary" :disabled="newCounterName === ''">
            + <span class="d-none d-md-inline">Add counter</span>
          </button>
        </div>
        <button @click="removeCounter" class="btn btn-danger" v-if="counters > 0">
          - <span class="d-none d-md-inline">Remove counter</span>
        </button>
      </div>
    </div>
  </nav>
  <div class="border-bottom" v-for="i in counters">
    <div class="container">
      <div class="row">
        <counter :name="newCounterName" />
      </div>
    </div>
  </div>
</template>

<script>
import Counter from "./Counter.vue";

export default {
  components: {
    counter: Counter,
  },

  data() {
    return {
      /**
       * The number of counters to show
       * @var int
       */
      counters: 0,

      /**
       * Name of a new counter
       * @var string
       */
      newCounterName: ''
    }
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
    // Set focus on new counter name input field
    this.focusInput();
  },

  methods: {
    /**
     * Add counter
     */
    addCounter() {
      if (this.newCounterName === '') {
        // Do not add a counter if no name has been input
        return;
      }

      this.counters++;
    },

    /**
     * Remove last counter
     */
    removeCounter() {
      if (this.counters > 0) {
        this.counters--;
      }

      this.focusInput();
    },

    /**
     * Set focus on new counter name input field
     */
    focusInput() {
      document.getElementById('newCounterName').focus();
    }
  }
}
</script>