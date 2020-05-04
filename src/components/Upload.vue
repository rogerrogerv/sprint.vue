<template>
  <div id="upload_button">
    <label class="button">
      <input
        type="file"
        ngf-select="true"
        ng-model="new_files"
        ng-change="fs.uploadFiles(new_files)"
        accept="image/gif, image/jpeg, image/png"
        multiple
        onchange="{uploadPhoto}"
      />
      Upload
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
#upload_button {
  display: inline-block;
  align-self: center;
}
#upload_button input[type="file"] {
  display: none;
}
</style>
