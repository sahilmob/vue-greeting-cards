<template>
  <div class="row">
    <div class="col-sm-6 card edit-area">
      <cc-image-upload @displayImageChanged="imageName = $event"></cc-image-upload>
      <cc-section-completed></cc-section-completed>
    </div>
    <div class="col-sm-6 card card-display">
      <cc-image-output :displayImage="imageName" :containerHeight="350" :clearImageProp="clearImage"></cc-image-output>
    </div>
  </div>
</template>

<script>
import ImageUpload from "./ImageUpload";
import ImageOutput from "./ImageOutput";
import SectionCompleted from "./SectionCompleted";

export default {
  components: {
    ccImageUpload: ImageUpload,
    ccImageOutput: ImageOutput,
    ccSectionCompleted: SectionCompleted
  },
  methods: {
    clearImage() {
      if (this.imageName !== "") {
        this.imageName = "placeholder.png";
      }
    }
  },
  data() {
    return {
      imageName: ""
    };
  }
};
</script>

<style scoped>
.edit-area {
  background: #dffdff;
  padding: 20px;
  height: 500px;
  border: none;
}

.card-display {
  padding: 20px;
  height: 500px;
  border: none;
}
</style>
