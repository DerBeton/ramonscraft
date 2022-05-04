<template>
    <div class="navigation">
      <ul class="nav-list">
        <li class="nav-item"><nuxt-link to="/photo">Fotos</nuxt-link></li>
        <li class="nav-item"><nuxt-link to="/video">Videos</nuxt-link></li>
        <li class="nav-item"><nuxt-link to="/blog">Blog</nuxt-link></li>
      </ul>
    </div>
</template>

<script>

export default {

}
</script>

<style scoped>

.navigation {
    display: flex;
    max-width: 900px;
    margin: 20px auto;
    gap: 20px;
}

.nav-list {
    list-style: none;
    display: flex;
    padding: 0px;
    margin: auto;
}

.nav-item {
    padding: 5px 15px;
    font-size: 26px;
    color: #333333;
    font-weight: bold;
}

.nav-item a {
    color: #333333;
    opacity: 0.75;
}

.nav-item a:hover {
    color: #048ABF;
    opacity: 1;
}

.nav-item a.nuxt-link-active {
  color: #048ABF;
  opacity: 1;
}


@media only screen and (max-width: 620px) {
    .navigation {
        margin-top: 10px;
    }
}

</style>