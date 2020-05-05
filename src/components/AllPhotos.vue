<template>
  <div class="">
    <img
      :src="`data:image/jpg;base64, ${photo}`"
      alt="AllPhotosDiv"
      width="300"
      height="300"
      @click="$emit(`'displayOnePhoto', ${photo}`)"
    />
  </div>
</template>

<script>
export default {
  title: "All Photos",
  name: "AllPhotos",
  props: ["photo", "displayOnePhoto"]
};
</script>

<style scoped>
.photo {
  display: flex;
}
</style>
