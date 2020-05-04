<template>
  <div id="navbar">
    <home />
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
