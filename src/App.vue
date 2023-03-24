<template>
  <div class="color">
    <h2>Image Search</h2>
    <input type="text" v-model="SearchTerm" placeholder="Enter search term"><br>
    <button @click="searchImages">Search</button>
    <div v-if="ImageUrl">
      <img :src="ImageUrl" alt="Image result">
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      ApiKey: 'Your-Unsplash-API-Key',
      SearchTerm: '',
      ImageUrl: '',
    }
  },
  methods: {
    async searchImages() {
      const response = await fetch(`https://api.unsplash.com/photos/random/?client_id=${this.ApiKey}&query=${this.SearchTerm}`);
      const data = await response.json();
      this.ImageUrl = data.urls.regular;
    }
  }
}
</script>


<style>
.color {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
  background-color: aqua;
}
</style>