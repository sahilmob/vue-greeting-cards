<template>
  <div class="row image-container" :style="styleObject" @mouseover="showOptions=true" @mouseleave="showOptions=false">
    <transition name="scale">
      <button type="button" class="btn btn-danger btn-sm" v-show="showOptions" @click="clearImageProp">Remove Image</button>
    </transition>
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
        setDragable();
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

var setDragable = () => {
  $("#outputImage").draggable();
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

img {
  width: 150%;
  height: 150%;
}

@keyframes scale-in {
  0% {
    transform: scale(0);
  }
  100% {
    transform: scale(1);
  }
}

.scale-enter-active {
  animation: scale-in 0.5s;
}

.scale-leave-active {
  animation: scale-out 0.5s;
}

@keyframes scale-out {
  0% {
    transform: scale(1);
  }
  100% {
    transform: scale(0);
  }
}
</style>
