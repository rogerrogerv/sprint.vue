<template>
  <div id="upload_button">
    <label class="button">
      <input
        type="file"
        accept="image/gif, image/jpeg, image/png"
        @change="uploadImg"
      />
      Upload
    </label>
  </div>
</template>

<script>
import { saveObject } from "../../utils/index.js";

export default {
  name: "Upload",
  data: () => ({}),
  methods: {
    uploadImg(e) {
      saveObject(e.target.files[0]);
      alert("Image uploaded!");
    }
  }
};
</script>

<style scoped>
#upload_button {
  display: inline-block;
  align-self: center;
}
#upload_button input[type="file"] {
  display: none;
}
</style>
