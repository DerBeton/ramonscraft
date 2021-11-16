<template>
    <section class="video-list">

        <CoolLightBox 
        :items="videos" 
        :index="index"
        :slideshow="false"
        :thumbnail="false"
        @close="index = null">
        </CoolLightBox>
              
        <div v-for="(video, videoIndex) in videos" :key="videoIndex" @click="index = videoIndex" class="video-thumbnail-wrapper">
            <div class="video-preview">
                <img class="video-thumbnail" :alt="video.title" :src="video.thumb" />
            </div>
            <div class="video-description">
                <h3>{{ video.title }}</h3>
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

.images {
  cursor: pointer;
  width: 300px;
  height: 300px;
  margin: 0 auto;
}

h1 {
    width: 100%;
    text-align: center;
}

.video-list {
    max-width: 900px;
    margin: 20px auto 20px auto;
    display: flex;
    flex-wrap: wrap;
    row-gap: 10px;
    column-gap: 10px;
    justify-content: center;
}

.video-thumbnail {
    width: 100%;
    height: auto;
    object-fit: cover;
}

.video-preview {
    max-height: 162px;
    overflow: hidden;
}

.video-thumbnail-wrapper {
    max-width: 288px;
    max-height: 288px;
    float: left;
    position: relative;
    color: #fff;
    cursor: pointer;
    overflow: hidden;
}

.video-description h3 {
    display: none;
    color: #048ABF;
    margin-top: 5px;
    font-weight: 500;
}

/* Only for devices with a limited accuracy pointing device */

@media (hover: hover) {
    .video-thumbnail {
        transition: transform .4s ease-in-out, filter .4s ease-in-out;
    }
    .video-thumbnail:hover {
        transform: scale(1.05);
    }   
}

@media only screen and (max-width: 935px) {
    .video-thumbnail-wrapper {
        width: 32%;
        float: left;
        position: relative;
        color: #fff;
        cursor: pointer;
        overflow: hidden;
    }
    .video-thumbnail {
    height: auto;
    }
    .video-preview {
        height: 100%;
        width: 100%;
        display: block;
        margin-bottom: -5px;
    }
    .video-list {
        width: 95%;
        row-gap: 5px;
        column-gap: 5px;
    }
}

/* Tutorial : https://codepen.io/GeorgePark/pen/VXrwOP */

/* ####### responsive ####### */

@media only screen and (max-width: 935px) {
    .video-thumbnail-wrapper {
        width: 32%;
        float: left;
        position: relative;
        color: #fff;
        cursor: pointer;
        overflow: hidden;
    }
    .video-thumbnail {
    height: auto;
    }
    .video-preview {
        height: 100%;
        width: 100%;
        display: block;
        margin-bottom: -5px;
    }
    .video-list {
        width: 95%;
        row-gap: 5px;
        column-gap: 5px;
    }
}


@media only screen and (max-width: 620px) {
    .video-thumbnail-wrapper {
        width: 48%;
    }
}

</style>