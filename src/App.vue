<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <Header @pageWasChanged="currentPage = $event"></Header>
        <keep-alive>
          <component :is="currentPage"></component>
        </keep-alive>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import CardFront from "./components/card/CardFront";
import CardInsideLeft from "./components/card/CardInsideLeft";
import CardInsideRight from "./components/card/CardInsideRight";
import CardBack from "./components/card/CardBack";

export default {
  data() {
    return {
      currentPage: "cardFront"
    };
  },
  components: {
    Header,
    CardFront,
    CardInsideLeft,
    CardInsideRight,
    CardBack
  }
};
</script>

<style>
body {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  color: #333;
}
</style>
