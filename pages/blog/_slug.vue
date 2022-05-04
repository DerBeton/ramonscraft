<template>
    <section class="articledetail">
        <div class="main-wrapper">
            <img @click="log" :src="image" alt="" class="article-mainimage">
            <div v-html="text" class="article-text"></div>
        </div>
    </section>
</template>

<script>

export default {
  transition: 'slide',
  scrollToTop: false,
  layout: 'article',
  methods: {
      log() {
          console.log(this.text);
      }
  },
  asyncData(context) {
      return context.app.$storyapi.get("cdn/stories/blog/" + context.params.slug, {
      }).then(res => {
    
          var article = res.data.story.content;

        return {
            title: article.title,
            image: article.image.filename + '/m/0x600',
            text: article.long_text ? context.app.$storyapi.richTextResolver.render(article.long_text) : ''
        }

      })
  },
}
</script>

<style>

.articledetail {
    max-width: 900px;
    margin: 20px auto 20px auto;
}

.article-mainimage {
    max-width: 100%;
}

.main-wrapper {
    margin: 0;
    min-height: calc(25vh + 70px);
}

h1 {
    margin: 20px 0;
    font-size: 36px;
    width: 100%;
}

h2 {
    margin: 20px 0;
    font-size: 32px;
}

.article-text {
    font-size: 16px;
    font-weight: lighter;
    line-height: 1.4;
}

.article-text img {
    max-width: 100%;
}

.slide-enter-active, .slide-leave-active { transition: opacity .5s; }
.slide-enter, .slide-leave-active { opacity: 0; }

</style>