<template>
  <div id="app" @changeView="this.title = 'Help Me!'">
    {{ title }}
    <navbar />
    <div v-if="currentView === 'allPhotos'">
      <div v-for="photo in this.photos" :key="photo.id">
        <allPhotos :photo="photo" v-on:displayOnePhoto="displayOnePhoto" />
      </div>
    </div>
    <div v-else>
      <singlePhoto :selectedPhoto="selectedPhoto" />
    </div>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import AllPhotos from "./components/AllPhotos";
import SinglePhoto from "./components/SinglePhoto";
import { listObjects, getSingleObject } from "../utils/index.js";

export default {
  name: "App",
  components: {
    navbar: Navbar,
    allPhotos: AllPhotos,
    singlePhoto: SinglePhoto
  },
  data: () => ({
    title: "Test AllPhotos",
    currentView: "allPhotos",
    photos: [],
    selectedPhoto: ""
  }),
  async created() {
    await this.getPhotos();
  },
  methods: {
    view() {
      this.currentView = "allPhotos";
    },
    displayOnePhoto(photo) {
      this.selectedPhoto = photo;
      this.currentView = "singlePhoto";
    },
    async getPhotos() {
      let list = await listObjects();
      const base64Array = list.map(obj => {
        const key = obj.Key;
        return getSingleObject(key);
      });
      Promise.all(base64Array).then(item => {
        this.photos = item;
      });
    }
  }
};
</script>

<style>
html,
body,
#app {
  height: 100%;
  margin: 0;
}

#app {
  padding: 1rem;
  font-family: Verdana, sans-serif;
  background: linear-gradient(to bottom, #5e81ac 5%, #d8dee9 100%);
  border: 1px solid black;
  display: flex;
  flex-direction: column;
}
.button {
  background: linear-gradient(to bottom, #81a1c1 5%, #5e81ac 100%);
  background-color: #81a1c1;
  border-radius: 10px;
  border: 1px solid #4c566a;
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
