<template>
  <div class=" m-8">
    <div class=" grid grid-cols-3      ">
      <div v-for="(album ,index) in albums" :key="index" class="p-8 h-64">
        <n-link class="m-auto" :to="'/photos/'+album.id">
          <!-- <div>       userId  {{ album.userId }}</div>  https://jsonplaceholder.typicode.com/photos?albumId=6-->
          <div>     album id     {{ album.id }}</div>
          <div>     title {{ album.title }}</div>
        </n-link>
      </div>
    </div>
    <!-- <div class="">
      <div v-for="photo in photos" :key="photo" class="">
        {{ photo }}
      </div>
    </div> -->
  </div>
</template>

<script>
export default {
  data () {
    return {
      albums: [],
      photos: []
    }
  },
  mounted () {
    this.getAlbums()
  //  this.getPhotos()
  },
  methods: {
    async getAlbums () {
      const result = await this.$axios.get('https://jsonplaceholder.typicode.com/albums')

      this.albums = result.data
    }
    //,
    // async  getPhotos () {
    //   const response = await this.$axios.get('https://jsonplaceholder.typicode.com/photos')

    //   this.photos = response.data
    // }
  }
}
</script>
