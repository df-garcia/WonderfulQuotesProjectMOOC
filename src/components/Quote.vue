<template>
  <div>
    <div class="col mb-4">
      <summary class="card" style="width: 16rem;">
        <div class="card-body">
          <p class="card-text">{{ text }}</p>
        </div>
      </summary>
    </div>
  </div>
</template>

<script>
export default {
  props: ["quoteText"],
  data() {
    return {
      text: this.quoteText,
    };
  },
};
</script>

<style scoped>
.card-text {
  font-family: "Arizonia", Arial !important;
  font-size: 150%;
}
</style>