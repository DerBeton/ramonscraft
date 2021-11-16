<template>
    <section class="homepage">
        <h1>Sorry, aber du bisch do falsch glandet...</h1>
    </section>
</template>

<script>

export default {
    middleware({redirect}) {
        return redirect('/photo')
      }
}

</script>
