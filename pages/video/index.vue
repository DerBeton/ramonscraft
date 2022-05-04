<template>
    <div class="main-wrapper">
        <VideoList :videos="loadedVideos" />
    </div>
</template>

<script>
import VideoList from '@/components/Video/VideoList.vue';

export default {

  components: {
    VideoList
  },
  transition: 'slide',
  scrollToTop: false,
  methods: {
      
  },
  asyncData(context) {
      return context.app.$storyapi.get("cdn/stories/", {
          version: "published",
          starts_with: "videos/",
          sort_by: "position"
      }).then(res => {
          
          return { 
              loadedVideos: res.data.stories.map(video => {
              return {
                  title: video.content.title,
                  description: video.content.description,
                  thumb: video.content.thumb.filename + '/m/293x0',
                  src: video.content.src.url
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
    min-height: 25vh;
}

h1 {
    width: 100%;
    text-align: center;
}

.slide-enter-active, .slide-leave-active { transition: opacity .5s; }
.slide-enter, .slide-leave-active { opacity: 0; }

</style>