<template>
    <section class="video-list">

        <CoolLightBox 
        :items="videos" 
        :index="index"
        :slideshow="false"
        :thumbnail="false"
        @close="index = null">
        </CoolLightBox>

        <div class="video-wrapper">
              
            <div v-for="(video, videoIndex) in videos" :key="videoIndex" @click="index = videoIndex" class="video-thumbnail-wrapper">
                <div class="video-preview">
                    <img class="video-thumbnail" :alt="video.title" :src="video.thumb" />
                </div>
                <div class="video-description">
                    <h3>{{ video.title }}</h3>
                </div>
            </div>

        </div>

    </section>
</template>

<script>
import CoolLightBox from 'vue-cool-lightbox';
import 'vue-cool-lightbox/dist/vue-cool-lightbox.min.css';

export default {
    components: {
        CoolLightBox
    },
    props: {
        videos: {
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

.video-list {
    max-width: 900px;
    margin: 20px auto 20px auto;
}

.video-wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    margin: -5px; 
}

.video-thumbnail-wrapper {
    width: 33.3%;
    padding: 5px;
    float: left;
    position: relative;
    color: #fff;
    cursor: pointer;
    overflow: hidden;
}

.video-preview {
    position: relative;
    overflow: hidden;
}

.video-preview::before {
    content: "";
    display: block;
    padding-top: calc(100% / 16 * 9);
}

.video-thumbnail {
    width: 100%;
    height: 100%;
    position: absolute;
    inset: 0;
    transition: transform .4s ease-in-out, filter .4s ease-in-out;
    transform-origin: center;
}  

.video-thumbnail:hover {
    transform: scale(1.05);
}

.video-description {
    display: none;
}

.video-description h3 {
    display: none;
    color: #048ABF;
    margin-top: 5px;
    font-weight: 500;
}

/* ####### responsive ####### */

@media only screen and (max-width: 935px) {
    .video-wrapper {
        margin: -2px; 
    }

    .video-thumbnail-wrapper {
        padding: 2px;
    }

    .video-thumbnail-wrapper {
        width: 50%;
    }

}

</style>