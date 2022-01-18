<template>
    <section class="image-card">
      <div class="card" v-for="(item, index) in photoUrls" :key="{index}">
        <img :src="item.small" alt="" class="photo">
      </div>
    </section>
</template>

<script>
export default {
  name: 'Card',
   data() {
    return {
      photoUrls: [],
      names: []
    }
    },
    created() {
      this.getUnsplashPhotos()
      this.searchPhotos()
  },
   methods: {
    getUnsplashPhotos() {
     const headers = { "Authorization": "Client-ID jF5H3GQKQhaKdSecL9UestPChaSxMAaUaUps5oXopbc"};
  fetch("https://api.unsplash.com/photos",  { headers })
    .then(response => response.json())
    .then(data => {
        console.log('data: ', data)
        const photos = data;
  if (photos) {
        this.photoUrls = photos.map(p => p.urls);
      }
    })
    .catch(error => console.log('error: ', error))
  }
  },
  searchPhotos() {
     const headers = { "Authorization": "Client-ID jF5H3GQKQhaKdSecL9UestPChaSxMAaUaUps5oXopbc"};
     fetch("https://api.unsplash.com/search/photos",  { headers })
    .then(response => response.json())
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.image-card{
  display: flex;
  flex-wrap: wrap;
  margin: -2% 0 0 30%;
}
.card{
  margin: 0 2% 2% 0;
}
.photo{
  width: 14vw;
  height: 30vh;
  border-radius: 5px;
}
</style>