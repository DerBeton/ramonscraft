<template>
    <div class="main-wrapper">
        <PhotoList :photos="loadedPhotos" />
    </div>
</template>

<script>
import PhotoList from '@/components/Photo/PhotoList.vue';

export default {
  components: {
    PhotoList
  },
  transition: 'slide',
  scrollToTop: false,
  methods: {
      
  },
  asyncData(context) {
      return context.app.$storyapi.get("cdn/stories/", {
          version: "published",
          starts_with: "photos/"
      }).then(res => {
          // console.log(res.data);

          return { 
              loadedPhotos: res.data.stories.map(photo => {
              return {
                  title: photo.content.title,
                  description: photo.content.description,
                  thumb: photo.content.thumb.filename || photo.content.src.filename + '/m/320x320',
                  src: photo.content.src.filename + '/m/'
              }
          })
        }
      })
  },
  computed: {
      redirectToPhotos() {
          this.$router.push('/photo');
    }
  }
}
</script>

<style scoped>

.main-wrapper {
    margin: 0 10px;
    min-height: calc(25vh + 70px);
}

h1 {
    width: 100%;
    text-align: center;
}

.slide-enter-active, .slide-leave-active { transition: opacity .5s; }
.slide-enter, .slide-leave-active { opacity: 0; }

</style>