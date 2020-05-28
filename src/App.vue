<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <new-quote @quoteAdded="addQuote"></new-quote>
    <all-quotes :quotes="quotes" @quoteDeleted="deleteQuote"></all-quotes>
    <div class="row">
      <div class="col-xs-12">
        <div class="alert alert-info text-center">Info: Click on Quote to DELETE it!</div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import QuoteGrid from "./components/QuoteGrid.vue";
import NewQuote from "./components/NewQuote.vue";
export default {
  data() {
    return {
      quotes: ["My first Quote"],
      maxQuotes: 10
    };
  },
  components: {
    allQuotes: QuoteGrid,
    newQuote: NewQuote,
    appHeader: Header
  },
  methods: {
    addQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        return alert("Delete some Quotes First!");
      }
      this.quotes.push(quote);
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  }
};
</script>

<style>
</style>
