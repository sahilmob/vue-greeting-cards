<template>
    <div class="row image-container" :style="styleObject">
        <img id="outputImage">
    </div>
</template>

<script>
import Firebase from "firebase";

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
  watch: {
    displayImage() {
      var storageRef = Firebase.storage().ref(
        "user_uploads/" + this.displayImage
      );
      storageRef.getDownloadURL().then(url => {
        document.getElementById("outputImage").src = url;
      });
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
