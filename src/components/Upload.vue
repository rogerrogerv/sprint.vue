<template>
  <div id="upload_button">
    <label>
      <input
        type="file"
        ngf-select="true"
        ng-model="new_files"
        ng-change="fs.uploadFiles(new_files)"
        accept="image/gif, image/jpeg, image/png"
        multiple
        onchange="{uploadPhoto}"
      />
      <span class="button upload">Upload</span>
    </label>
  </div>
</template>

<script>
export default {
  name: "Upload",
  data: () => ({})
};
</script>

<style scoped>
.upload {
  background-color: aquamarine;
}

#upload_button {
  display: inline-block;
}
#upload_button input[type="file"] {
  display: none;
}
</style>
