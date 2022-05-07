<template>
    <div class="main-wrapper">
        <BlogList :articles="loadedArticles" />
    </div>
</template>

<script>
import BlogList from '@/components/Blog/BlogList.vue';

export default {
  components: {
    BlogList
  },
  transition: 'slide',
  scrollToTop: false,
  methods: {
      
  },
  asyncData(context) {
      return context.app.$storyapi.get("cdn/stories/", {
          version: "published",
          starts_with: "blog/"
      }).then(res => {          
          return { 
              loadedArticles: res.data.stories.map(article => {
              return {
                  title: article.content.title,
                  intro: article.content.intro,
                  tags: article.tag_list,
                  thumb: article.content.image.filename + '/m/300x185',
                  src: article.content.image.filename + '/m/',
                  slug: article.slug,
                  link: 'blog/' + article.slug
              }
          })
        }
      })
  },
  computed: {
      redirectToPhotos() {
          this.$router.push('/blog');
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