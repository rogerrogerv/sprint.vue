<template>
  <div id="home">
    <button @click="$emit('AllPhotos')" class="button">Home</button>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
  data: () => ({
    title: ""
  })
};
</script>

<style></style>
