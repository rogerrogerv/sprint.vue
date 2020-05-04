<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>{{ title }}</h1>
    <allPhotos />
    <navbar v-on:AllPhotos="getPhotos(photos)" />
    <div v-for="(index, photo) in photos" :key="index">
      <allPhotos :source="photo" />
      <img
        alt="!!!test!!!"
        src="data:image/jpg;base64, "
      />
    </div>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import AllPhotos from "./components/AllPhotos";
import { listObjects, getSingleObject } from "../utils/index.js";

export default {
  name: "App",
  components: {
    navbar: Navbar,
    allPhotos: AllPhotos
  },
  data: () => ({
    title: "Photo Uploads",
    view: "allPhotos",
    photos: []
  }),
  methods: {
    getPhotos: async function() {
      let list = await listObjects();
      const base64Array = list.map(obj => {
        const key = obj.Key;
        return getSingleObject(key);
      });
      return Promise.all(base64Array);
    }
  },
  created: function() {
    this.getPhotos().then(item => {
      console.log("item:", item);
      this.photos = [...this.photos, item];
      console.log("this.photos:----------->", this.photos[0][0]);
    });
  }
};
</script>

<style>
#app {
  padding: 1rem;
  font-family: Verdana, sans-serif;
  justify-content: space-between;
  background: linear-gradient(to bottom, #5e81ac 5%, #81a1c1 100%);
}
.button {
  background: linear-gradient(to bottom, #81a1c1 5%, #5e81ac 100%);
  background-color: #81a1c1;
  border-radius: 10px;
  border: 1px solid #4c566a;
  display: inline-block;
  cursor: pointer;
  color: #eceff4;
  font-size: 19px;
  padding: 12px 37px;
  text-decoration: none;
  text-shadow: 0px 1px 0px #2e3440;
}
.button:hover {
  background: linear-gradient(to bottom, #5e81ac 5%, #81a1c1 100%);
  background-color: #81a1c1;
}
.button:active {
  position: relative;
  top: 2px;
}
</style>
