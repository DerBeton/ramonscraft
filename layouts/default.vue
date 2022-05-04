<template>
    <div>
        <Landing />
        <Navigation />
        <Nuxt />
    </div>
        
</template>

<script>
import Landing from '@/components/Landing.vue';
import Navigation from '~/components/Navigation.vue';

export default {
    components: {
        Landing,
        Navigation
    }
} 

</script>

<style>


</style>
