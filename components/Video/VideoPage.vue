<template>
    <div class="main-wrapper">
        <Landing />
        <h1 id="video-anchor">Videos</h1>
        <VideoList :videos="loadedVideos" />
    </div>
</template>

<script>
import Landing from '@/components/Landing.vue';
import VideoList from '@/components/Video/VideoList.vue';

export default {

  components: {
    Landing,
    VideoList
  },
  methods: {
      
  },
  asyncData(context) {
      return context.app.$storyapi.get("cdn/stories/", {
          version: "published",
          starts_with: "videos/",
          sort_by: "position"
      }).then(res => {
          console.log(res.data);

          return { 
              loadedVideos: res.data.stories.map(video => {
              return {
                  title: video.content.title,
                  description: video.content.description,
                  thumb: video.content.thumb.filename + '/m/288x0',
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
    
}

h1 {
    width: 100%;
    text-align: center;
}

</style>