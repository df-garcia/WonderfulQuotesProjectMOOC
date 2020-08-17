<template>
  <div>
    <h4>
      <b>Quote</b>
    </h4>
    <div class="form-group">
      <textarea
        v-model="newQuoteText"
        class="form-control"
        id="exampleFormControlTextarea1"
        rows="3"
      ></textarea>
    </div>
    <div class="col-md-12 text-center">
      <button @click="addNewQuote" type="button" class="btn btn-primary">Add Quote</button>
    </div>
    <br />
    <div v-if="showAlert" class="alert alert-warning text-center" role="alert">You can not add more than 10 quotes</div>
    <br v-if="showAlert" />
  </div>
</template>

<script>
import { eventBus } from "../main.js";
export default {
  props: ["quotesArray"],
  data() {
    return {
      newQuoteText: "",
    };
  },
  computed: {
    array: function () {
      return this.quotesArray;
    },
    showAlert: function(){
        return (this.array.length == 10);
    }
  },
  methods: {
    addNewQuote() {
      if (this.array.length < 10) {
        eventBus.$emit("newQuoteAdded", this.newQuoteText);
        this.newQuoteText = "";
      } 
    },
  },
};
</script>

<style>
</style>