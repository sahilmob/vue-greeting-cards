<template>
  <div class="row">
    <div class="col-sm-6 card edit-area">
      <cc-text-input @displayTextChanged="textBox1 = $event"></cc-text-input>
      <cc-image-upload></cc-image-upload><hr>
      <cc-text-input @displayTextChanged="textBox2 = $event"></cc-text-input>
      <cc-text-input @displayTextChanged="textBox3 = $event"></cc-text-input>
    </div>
    <div class="col-sm-6 card card-display">
      <cc-text-output :displayText="textBox1" :containerHeight="130"></cc-text-output>
      <cc-text-output :displayText="textBox2" :containerHeight="130"></cc-text-output>
      <cc-text-output :displayText="textBox3" :containerHeight="130"></cc-text-output>
    </div>
  </div>
</template>

<script>
import TextInput from "./TextInput";
import TextOutput from "./TextOutput";
import ImageUpload from "./ImageUpload";

export default {
  components: {
    ccTextInput: TextInput,
    ccTextOutput: TextOutput,
    ccImageUpload: ImageUpload
  },
  data() {
    return {
      textBox1: "",
      textBox2: "",
      textBox3: ""
    };
  }
};
</script>

<style scoped>
.edit-area {
  background: #dffdff;
  padding: 20px;
  height: 800px;
  border: none;
}

.card-display {
  padding: 20px;
  height: 800px;
  border: none;
}
</style>
