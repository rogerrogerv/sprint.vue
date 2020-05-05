<template>
  <div id="home">
    <button @click="$emit('view')" class="button">Home</button>
    <button @click="changeView()" class="button">TEST</button>
  </div>
</template>

<script>
export default {
  name: "Home",
  props: ["view"],
  methods: {
    changeView() {
      this.$emit("changeView");
    }
  },
  components: {},
  data: () => ({})
};
</script>

<style></style>
