<template>
    <section class="photo-list">

        <CoolLightBox 
        :items="photos" 
        :index="index"
        :slideshow="false"
        :thumbnail="false"
        @close="index = null">
        </CoolLightBox>
              
        <div class="photo-wrapper">

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

.photo-list {
    max-width: 900px;
    margin: 20px auto 20px auto;
}

.photo-wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    margin: -5px; 
}

.photo-thumbnail-wrapper {
    width: 33.3%;
    padding: 5px;
    float: left;
    position: relative;
    color: #fff;
    cursor: pointer;
    overflow: hidden;
}

.photo-preview {
    position: relative;
    overflow: hidden;
}

.photo-preview::before {
    content: "";
    display: block;
    padding-top: 100%;
}

.photo-thumbnail {
    width: 100%;
    height: 100%;
    position: absolute;
    inset: 0;
    transition: transform .4s ease-in-out, filter .4s ease-in-out;
    transform-origin: center;
}  

.photo-thumbnail:hover {
    transform: scale(1.05);
}

/* ####### responsive ####### */

@media only screen and (max-width: 935px) {
    .photo-wrapper {
        margin: -2px; 
    }

    .photo-thumbnail-wrapper {
        padding: 2px;
    }

}

</style>