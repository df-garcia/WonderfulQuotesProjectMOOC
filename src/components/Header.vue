<template>
  <div>
    <br />
    <h1>
      <b>Quotes Added</b>
    </h1>

    <div class="progress">
      <div
        class="progress-bar"
        role="progressbar"
        :style="{'width': quotesWidth + '%'}"
        aria-valuenow="25"
        aria-valuemin="0"
        aria-valuemax="100"
      >{{ numberOfQuotes }}/10</div>
    </div>
    <br />
  </div>
</template>

<script>
export default {
  props: ["numberOfQuotes"],
  computed: {
    quotesWidth: function () {
      return this.numberOfQuotes * 10;
    },
  },
};
</script>

<style scoped>
</style>