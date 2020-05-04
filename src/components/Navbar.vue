<template>
  <div id="navbar">
    <div>
      <button @click="$emit('AllPhotos')" class="button">Home</button>
    </div>
    <div>
      <upload />
      <h1>{{ title }}</h1>
    </div>
  </div>
</template>

<script>
import Upload from "./Upload";

export default {
  name: "Navbar",
  components: {
    upload: Upload
  },
  data: () => ({
    title: "All Photos"
  })
};
</script>

<style scoped>
#navbar {
  background-color: lightskyblue;
  display: flexbox;
  flex-direction: row;
  justify-content: space-between;
}
</style>
