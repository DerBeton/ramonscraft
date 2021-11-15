<template>
    <div class="main-wrapper">
        <Landing />
        <h1 id="photo-anchor">Photos</h1>
        <PhotoList :photos="loadedPhotos" />
    </div>
</template>

<script>
import Landing from '@/components/Landing.vue';
import PhotoList from '@/components/Photo/PhotoList.vue';

export default {

  components: {
    Landing,
    PhotoList
  },
  methods: {
      
  },
  asyncData(context) {
      return context.app.$storyapi.get("cdn/stories/", {
          version: "draft",
          starts_with: "photos/"
      }).then(res => {
          // console.log(res.data);
          return { 
              loadedPhotos: res.data.stories.map(photo => {
              return {
                  title: photo.content.title,
                  description: photo.content.description,
                  thumb: photo.content.thumb.filename,
                  src: photo.content.src.filename
              }
          })
        }
      })
  },
}
</script>

<style scoped>

.main-wrapper {
    margin: 0;
    
}

h1 {
    width: 100%;
    text-align: center;
}

</style>