<template>
  <div>
    <div class="row row-cols-1 row-cols-md-4">
      <quote
        v-for="(quote, i) in quotesArray"
        :key="i"
        :quoteText="quote.text"
        @click.native="deleteQuote(i)"
      ></quote>
    </div>
  </div>
</template>

<script>
import Quote from "./Quote.vue";
import { eventBus } from "../main.js"
export default {
  props: ["quotesArray"],
  data() {
    return {
      quotes: this.quotesArray,
    };
  },
  methods: {
    deleteQuote(index) {
      eventBus.$emit('quoteDeleted', index);
    },
  },
  components: {
    quote: Quote,
  },
};
</script>

<style scoped>
</style>