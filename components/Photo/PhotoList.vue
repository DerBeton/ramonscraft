<template>
    <section class="photo-list">

        <CoolLightBox 
        :items="photos" 
        :index="index"
        :slideshow="false"
        :thumbnail="false"
        @close="index = null">
        </CoolLightBox>
              
        <div v-for="(photo, photoIndex) in photos" :key="photoIndex" @click="index = photoIndex" class="photo-thumbnail-wrapper">
            <div class="photo-preview">
                <img class="photo-thumbnail" :alt="photo.title" :src="photo.thumb" />
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
        photos: {
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

.photo-list {
    max-width: 900px;
    margin: 20px auto 20px auto;
    display: flex;
    flex-wrap: wrap;
    row-gap: 10px;
    column-gap: 10px;
    justify-content: center;
}

.photo-thumbnail {
    width: 100%;
    height: auto;
    object-fit: cover;
}

.photo-thumbnail-wrapper {
    max-width: 288px;
    max-height: 288px;
    float: left;
    position: relative;
    color: #fff;
    cursor: pointer;
    overflow: hidden;
}

/* Only for devices with a limited accuracy pointing device */

@media (hover: hover) {
    .photo-thumbnail {
        transition: transform .4s ease-in-out, filter .4s ease-in-out;
        filter: blur(1.5px);
    }
    .photo-thumbnail:hover {
        transform: scale(1.05);
        filter: blur(0);
    }   
}

@media only screen and (max-width: 935px) {
    .photo-thumbnail-wrapper {
        width: 32%;
        float: left;
        position: relative;
        color: #fff;
        cursor: pointer;
        overflow: hidden;
    }
    .photo-thumbnail {
    height: auto;
    }
    .photo-preview {
        height: 100%;
        width: 100%;
        display: block;
        margin-bottom: -5px;
    }
}

/* Tutorial : https://codepen.io/GeorgePark/pen/VXrwOP */

/* ####### responsive ####### */

@media only screen and (max-width: 935px) {
  .photo-list {
    width: 95%;
    row-gap: 5px;
    column-gap: 5px;
  }
}
/*
@media only screen and (max-width: 900px) {
    .photo-list {
        display: initial;
    }
}
*/
</style>