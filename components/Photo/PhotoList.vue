<template>
    <section class="photo-list">

        <CoolLightBox 
        :items="photos" 
        :index="index"
        :slideshow="false"
        :thumbnail="false"
        @close="index = null">
        </CoolLightBox>
              
        <div class="photos-wrapper">

            <div v-for="(photo, photoIndex) in photos" :key="photoIndex" @click="index = photoIndex" class="photo-thumbnail-wrapper">
                <div class="photo-preview">
                    <img class="photo-thumbnail" :alt="photo.title" :src="photo.thumb" />
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

h1 {
    width: 100%;
    text-align: center;
}

.photos-wrapper {
    /* margin: 20px auto 20px auto; */
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    margin: -5px; 
}

.photo-list {
    max-width: 900px;
    margin: 20px auto 20px auto;
}

.photo-thumbnail {
    width: 100%;
    height: auto;
    object-fit: cover;
    transition: transform .4s ease-in-out, filter .4s ease-in-out;
    transform-origin: center;
}

.photo-thumbnail:hover {
        transform: scale(1.05);
}   



.photo-thumbnail-wrapper {
    padding: 5px;
    float: left;
    position: relative;
    color: #fff;
    cursor: pointer;
    overflow: hidden;
}

.photo-preview {
    max-width: 293px;
    max-height: 293px;
    overflow: hidden;
}

/* Only for devices with a limited accuracy pointing device */

@media (hover: hover) and (pointer: fine) {
    .photo-thumbnail {
        transition: transform .4s ease-in-out, filter .4s ease-in-out;
        /*filter: blur(1.5px);*/
    }
    .photo-thumbnail:hover {
        transform: scale(1.05);
        /*filter: blur(0);*/
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

/* ####### responsive ####### */

@media only screen and (max-width: 935px) {
  .photo-list {
    width: 95%;
    row-gap: 5px;
    column-gap: 5px;
  }
}

</style>