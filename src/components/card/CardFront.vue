<template>
  <div class="row">
    <div class="col-sm-6 card edit-area">
      <cc-text-input></cc-text-input>
      <cc-text-input></cc-text-input>
      <cc-text-input></cc-text-input>
    </div>
    <div class="col-sm-6 card card-display"></div>
  </div>
</template>

<script>
import TextInput from "./TextInput";

export default {
  components: {
    ccTextInput: TextInput
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
