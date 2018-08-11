<template>
    <div class="row">
        <div class="col-sm-12">
            <h4>Upload image:</h4>
            <div class="form-group">
                <input type="file" id="fileUpload" class="form-control-file" @change="uploadFile">
                <progress value="0" max="100" id="progressBar"></progress>
                <br>
                <img id="image">
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
      var upload = storageRef.put(this.file);
      var reader = new FileReader();
      reader.readAsDataURL(this.file);
      reader.onload = e => {
        document.getElementById("image").src = e.target.result;
      };
      upload.on("state_changed", snapshot => {
        var progress = snapshot.bytesTransferred / snapshot.totalBytes * 100;
        document.getElementById("progressBar").value = progress;
        if (progress == 100) {
          this.$emit("displayImageChanged", this.file.name);
        }
      });
    }
  }
};
</script>

<style scoped>
img {
  max-width: 200px;
}
</style>
