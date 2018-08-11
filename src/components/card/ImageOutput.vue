<template>
  <div class="row image-container" :style="styleObject" @mouseover="showOptions=true" @mouseleave="showOptions=false">
    <button type="button" class="btn btn-danger btn-sm" v-show="showOptions" @click="clearImageProp">Remove Image</button>
    <img id="outputImage">
  </div>
</template>

<script>
import Firebase from "firebase";

export default {
  data() {
    return {
      showOptions: false
    };
  },
  props: {
    displayImage: {
      type: String
    },
    containerHeight: {
      type: Number,
      default: 200
    },
    clearImageProp: Function
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

button {
  position: absolute;
  z-index: 1;
}
</style>
