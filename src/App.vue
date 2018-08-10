<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <Header></Header>
        <CardFront />
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import CardFront from "./components/card/CardFront";

export default {
  components: {
    Header,
    CardFront
  }
};
</script>

<style>
</style>
