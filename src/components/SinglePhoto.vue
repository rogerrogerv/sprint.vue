<template>
  <div>
    <img @displayOnePhoto="selectedPhoto($event)" 
      :src="`data:image/jpg;base64, ${image}`"
      alt="singlePicture"
    />
  </div>
</template>

<script>
export default {
  title: "Single Photo",
  name: "SinglePhoto",
  image: "",
  props: ["selectedPhoto"],
  methods: {
    displayOnePhoto(photo) {
      this.image = photo;
    }
  }
};
</script>

<style></style>
