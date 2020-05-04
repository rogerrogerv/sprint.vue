<template>
  <div class="photo">
    <img :src="'data:image/jpeg;base64, ', source" />
  </div>
</template>

<script>
export default {
  name: "AllPhotos",
  props: ["source"],
};
</script>

<style></style>
