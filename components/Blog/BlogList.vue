<template>
    <section class="blog-list">
        <div class="articles-wrapper">

            <article v-for="(article, articleIndex) in articles" :key="articleIndex" class="article">
                <nuxt-link :to="article.link" class="article-link">
                    <div class="article-thumbnail-wrapper">
                        <div class="article-preview">
                            <img class="article-thumbnail" :alt="article.title" :src="article.thumb" />
                        </div>
                    </div>

                    <div class="article-info">
                        <h2 class="article-title">{{ article.title }}</h2>
                        <p class="article-teaser">{{ article.intro }}</p>
                    </div>
                </nuxt-link>
            </article>

        </div>
    </section>
</template>

<script>

export default {
    props: {
        articles: {
            type: Array,
            required: true
        }
    },
    data() {
        return {
            index: null,
        };
    },
}


</script>

<style scoped>

.article {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    padding: 5px;
    width: 33.3%;
}

.articles-wrapper {
    /* margin: 20px auto 20px auto; */
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    margin: -5x;
}

h1 {
    width: 100%;
    text-align: center;
}

h2 {
    font-size: 24px;
}

.blog-list {
    max-width: 900px;
    margin: 20px auto;
}

.article-thumbnail {
    width: 100%;
    height: auto;
    object-fit: cover;
    transition: transform .4s ease-in-out, filter .4s ease-in-out;
    transform-origin: center;
}

.article-thumbnail:hover {
    transform: scale(1.05);
}   

.article-preview {
    max-height: 185px;
}

.article-thumbnail-wrapper {
    width: 100%;
    position: relative;
    color: #fff;
    cursor: pointer;
    overflow: hidden;
}

.article-title {
    margin: 6px 0;
}

.article-teaser {
    margin: 6px 0;
    color: #333;
    font-weight: lighter;
}


/* Only for devices with a limited accuracy pointing device */

@media (hover: hover) and (pointer: fine) {
    .article-thumbnail {
        transition: transform .4s ease-in-out, filter .4s ease-in-out;
        /*filter: blur(1.5px);*/
    }
    .article-thumbnail:hover {
        transform: scale(1.05);
        /*filter: blur(0);*/
    }   
}

/*

@media only screen and (max-width: 935px) {


    .article-thumbnail-wrapper {
        width: 32%;
        float: left;
        position: relative;
        color: #fff;
        cursor: pointer;
        overflow: hidden;
    }
    .article-thumbnail {
    height: auto;
    }
    .article-preview {
        height: 100%;
        width: 100%;
        display: block;
        margin-bottom: -5px;
    }
}

*/
/* ####### responsive ####### */

@media only screen and (max-width: 935px) {
  .article-list {
    width: 95%;
    row-gap: 5px;
    column-gap: 5px;
  }
}

</style>