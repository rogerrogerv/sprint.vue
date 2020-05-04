<template>
  <div class="photo">
    <img :src="data:image/jpeg;base64," + "source" alt="AllPhotosDiv"/>
  </div>
</template>

<script>
export default {
  name: "AllPhotos",
  props: ["source"]
};
</script>

<style scoped>
.photo {
  display: flex;
}
</style>
