<template>
  <div class="row">
    <div class="col-sm-6 card edit-area">
      <cc-text-input @displayTextChanged="textBox1 = $event"></cc-text-input>
      <cc-text-input @displayTextChanged="textBox2 = $event"></cc-text-input>
      <cc-text-input @displayTextChanged="textBox3 = $event"></cc-text-input>
      <cc-section-completed></cc-section-completed>
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
import SectionCompleted from "./SectionCompleted";

export default {
  components: {
    ccTextInput: TextInput,
    ccTextOutput: TextOutput,
    ccSectionCompleted: SectionCompleted
  },
  data() {
    return {
      textBox1: "",
      textBox2: "",
      textBox3: "",
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
