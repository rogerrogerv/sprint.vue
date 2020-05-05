<template>
  <div id="navbar">
    <home v-on:view="view" />
    <h1>{{ title }}</h1>
    <upload />
  </div>
</template>

<script>
import Upload from "./Upload";
import Home from "./Home";

export default {
  name: "Navbar",
  components: {
    upload: Upload,
    home: Home
  },
  data: () => ({
    title: "All Photos"
  })
};
</script>

<style scoped>
#navbar {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
</style>
