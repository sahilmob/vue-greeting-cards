<template>
    <div class="row">
        <div class="col-sm-12">
            <h4>Upload image:</h4>
            <div class="form-group">
                <input type="file" id="fileUpload" class="form-control-file" @change="uploadFile">
                <br>
                <img id="image">
                <button type="button" id="setImageButton">Set Image</button>
            </div>
        </div>
    </div>
</template>

<script>
import Firebase from "firebase";
export default {
  data() {
    return {
      file: ""
    };
  },
  methods: {
    uploadFile(event) {
      this.file = event.target.files[0];
      var storageRef = Firebase.storage().ref("user_uploads/" + this.file.name);
      storageRef.put(this.file);
    }
  }
};
</script>

<style>
</style>
