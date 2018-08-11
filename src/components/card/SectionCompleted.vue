<template>
    <div class="row">
        <div class="form-check form-check-inline">
            <div class="form-check-label">
                <input type="checkbox" class="form-check-input" v-model="checked" @click="sectionCompleted"> Mark section as completed
            </div>
        </div>
    </div>
</template>

<script>
import { EventBus } from "../../main";
export default {
  data() {
    return {
      checked: ""
    };
  },
  methods: {
    sectionCompleted() {
      EventBus.$emit("mark-as-completed", this.checked);
    }
  }
};
</script>

<style>
</style>
