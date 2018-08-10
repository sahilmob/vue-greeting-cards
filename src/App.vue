<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <Header @pageWasChanged="currentPage = $event"></Header>
        <component :is="currentPage"></component>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import CardFront from "./components/card/CardFront";

export default {
  data() {
    return {
      currentPage: "cardFront"
    };
  },
  components: {
    Header,
    CardFront
  }
};
</script>

<style>
body {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  color: #333;
}
</style>
