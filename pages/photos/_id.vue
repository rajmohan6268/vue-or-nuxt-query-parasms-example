<template class="">
  <div class=" grid grid-cols-3 h-64">
    <div v-for="(photo,index) in photos " :key="index" class="">
      <!-- {{ photo}} -->
      <div class="">
        albumId  {{ photo.albumId }}
      </div>
      <div class="">
        id {{ photo.id }}
      </div>
      <div class="">
        title  {{ photo.title }}
      </div>
      <!-- url  {{ photo.url }} -->
      <img class="w-40" :src="photo.url">
      <!-- thumbnailUrl{{ photo.thumbnailUrl }} -->
      <!-- <img class="w-40" :src="photo.thumbnailUrl"> -->
    </div>
  </div>
</template>
<script>
export default {}
</script>

<script>
export default {
  data() {
    return {
      photos: ""
    };
  },
  mounted() {
    console.log(this.$route.params.id);
    this.getPhotos();
  },
  methods: {
    async getPhotos() {
      const response = await this.$axios.get(
        `https://jsonplaceholder.typicode.com/photos?albumId=${this.$route.params.id}`
      );

      this.photos = response.data
    }
  }
};
</script>
