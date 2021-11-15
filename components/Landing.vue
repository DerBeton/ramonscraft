<template>
    <div id="landing">
        <section id="landing-box">
            <img id="ramon-rund" src="@/assets/img/ramon-rund.png" alt="Bild von Ramon">
            <h1 class="landing-heading">Ramon's Craft 🛠️</h1>
            <p>I am a web developer who loves to snap photos, make videos and work on some web projects. If you are interested in my work or have questions, feel free to ask me</p>
        </section>

    
    <svg @click="scrollToHeader" id="arrow-down" xmlns="http://www.w3.org/2000/svg" width="34.218" height="20.556" viewBox="0 0 34.218 20.556">
        <path id="Pfad_5" data-name="Pfad 5" d="M2159,826.52l16.527-18.383,16.2,18.383" transform="translate(2192.474 827.188) rotate(180)" fill="none" stroke="#048abf" stroke-width="2"/>
    </svg>

    </div>

</template>

<script>
export default {
    methods: {
        scrollToHeader() {

            /* scroll by window height */
            var clientHeight = document.documentElement.clientHeight;

            window.scrollBy({top: clientHeight, left: 0, behavior: "smooth"});
        }
    }
}
</script>

<style scoped>
    #landing {
        margin: 0;
        padding: 0;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    #landing-box {
        max-width: 900px;
        padding: 20px;
        text-align: center;
    }

    #ramon-rund {
        margin: 20px;
    }

    .landing-heading {
        margin: 0;
        font-size: 60px;
        font-weight: bolder;
    }

    p {
        font-size: 16px;
        font-weight: lighter;
    }

    #arrow-down {
        position: absolute;
        margin: 0 auto;
        padding: 20px;
        bottom: 0;
        cursor: pointer;
    }
</style>