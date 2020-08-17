<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <header-component :numberOfQuotes="numberOfQuotes"></header-component>
      </div>
    </div>
    <div class="row justify-content-center">
      <div class="col-sm-6 col-md-offset-3">
        <add-quote-component :quotesArray="quotesArray"></add-quote-component>
      </div>
    </div>
    <div class="row">
      <div class="col-sm-12">
        <quotes-component :quotesArray="quotesArray"></quotes-component>
      </div>
    </div>
    <div class="row">
      <div class="col-sm-12">
        <footer-component></footer-component>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import AddQuote from "./components/AddQuote.vue";
import Quotes from "./components/Quotes.vue";
import Footer from "./components/Footer.vue";
import { eventBus } from './main.js';
export default {
  data() {
    return {
      quotesArray: [
        {
          id: 0,
          text: "First Quote",
        },
        {
          id: 1,
          text: "This is just a test",
        },
      ],
    };
  },
  computed: {
      numberOfQuotes: function(){
          return this.quotesArray.length;
      }
  },
  created(){
      eventBus.$on('newQuoteAdded', (quoteText) => {
          this.quotesArray.push({id: this.quotesArray.length, text: quoteText});
      });
  },
  components: {
    "header-component": Header,
    "add-quote-component": AddQuote,
    "quotes-component": Quotes,
    "footer-component": Footer,
  },
};
</script>

<style>
</style>
