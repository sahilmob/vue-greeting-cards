<template>
    <div class="row image-container" :style="styleObject">
        <img id="outputImage">
    </div>
</template>

<script>
export default {
  props: {
    displayImage: {
      type: String
    },
    containerHeight: {
      type: Number,
      default: 200
    }
  },
  computed: {
    styleObject() {
      return {
        height: this.containerHeight + "px"
      };
    }
  }
};
</script>

<style>
.image-container {
  border: 1px dotted gray;
  overflow: hidden;
  margin: 5px 0;
}
</style>
