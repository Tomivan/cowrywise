<template>
    <section class="image-card">
      <div class="card" v-for="(item, index) in photoUrls" :key="{index}">
          <img :src="item.small" alt="" class="photo">
      </div>
      <div class="details" v-for="(item, index) in users" :key="{index}">
          <p>{{item.user.name}}</p>
          <p>{{item.user.location}}</p>
      </div>
    </section>
</template>

<script>
  // import VueContentLoading from 'vue-content-loading';
  export default {
  name: 'Card',
  // components: {
  //   VueContentLoading,
  // },
   data() {
    return {
      photoUrls: [],
      users: [],
      names: []
    }
    },
    created() {
      this.getUnsplashPhotos()
  },
   methods: {
    getUnsplashPhotos() {
     const headers = { "Authorization": "Client-ID J05MCgl8YDTlnEQRvSyg4mKnaEEU6iC6GSgc6etlexU"};
  fetch("https://api.unsplash.com/photos",  { headers })
    .then(response => response.json())
    .then(data => {
        console.log('data: ', data)
        const photos = data; 
  if (photos) {
        this.photoUrls = photos.map(p => p.urls);
      } else if (photos) {
        this.users = photos.map(p => p.user)
        console.log(photos.user)
      }
    })
    .catch(error => console.log('error: ', error))
  },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.image-card{
  display: flex;
  flex-wrap: wrap;
  margin: -1% 0 0 28%;
  width: 60%;
}
.card{
  margin: 0 2% 2% 0;
}
.photo{
  width: 14vw;
  height: 30vh;
  border-radius: 5px;
}

@media screen and (max-width: 768px){
  .photo{
    width: 60vw;
  }
  .image-card{
    margin-left: 20%;
  }
}
</style>