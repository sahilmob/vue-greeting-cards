<template>
  <div class="row">
    <div class="col-sm-6 card edit-area">
      <cc-text-input @displayTextChanged="textBox1 = $event"></cc-text-input>
    </div>
    <div class="col-sm-6 card card-display">
      <cc-text-output :displayText="textBox1" :containerHeight="750"></cc-text-output>
    </div>
  </div>
</template>

<script>
import TextInput from "./TextInput";
import TextOutput from "./TextOutput";
export default {
  data() {
    return {
      textBox1: ""
    };
  },
  components: {
    ccTextInput: TextInput,
    ccTextOutput: TextOutput
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
