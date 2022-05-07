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
                        <div class="article-tag-wrapper">
                            <span v-for="(tag, tagIndex) in article.tags" :key="tagIndex" class="article-tags">{{ tag + ' ' }}</span>
                        </div>
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

.articles-wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    margin: -5x;
}

.article {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    padding: 5px;
    width: 33.3%;
}

.article-thumbnail-wrapper {
    position: relative;
    color: #fff;
    cursor: pointer;
    overflow: hidden;
}

.article-thumbnail {
    width: 100%;
    height: 100%;
    position: absolute;
    inset: 0;
    transition: transform .4s ease-in-out, filter .4s ease-in-out;
    transform-origin: center;
} 

.article:hover .article-thumbnail {
    transform: scale(1.05);
}

.article-preview {
    position: relative;
    overflow: hidden;
}

.article-preview::before {
    content: "";
    display: block;
    padding-top: calc(100% / 16 * 9);
}

.article-info {
    display: flex;
    flex-direction: column;
}

.article-tag-wrapper {
    margin-top: 10px;
}

.article-tags {
    font-size: 14px;
    color: #333;
}

.article-title {
    margin: 6px 0;
    font-weight: 500;
}

.article-teaser {
    margin: 0;
    color: #333;
    font-weight: lighter;
}

/* ####### responsive ####### */

@media only screen and (max-width: 935px) {
    .blog-wrapper {
        margin: -2px; 
    }

    .blog-thumbnail-wrapper {
        padding: 2px;
    }

    .article {
        width: 50%;
    }

}


@media only screen and (max-width: 500px) {
    .article {
        width: 100%;
    }

}

</style>