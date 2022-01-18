<template>
  <div class="search">
     <div class="input">
        <i class="fa fa-search search-icon" aria-hidden="true"></i>
        <input type="text" placeholder="Search for photo" v-model="search">
      </div>
  </div>
</template>

<script>
export default {
  name: 'SearchPhoto'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.input{
  background: #c8c8c8;
  padding: 2em;
}
input{
  height: 7vh;
  width: 65vw;
  border: 1px solid #0000001e;
  border-radius: 5px;
  margin-left: 15%;
}
input::placeholder{
  padding-left: 1em;
}
</style>
