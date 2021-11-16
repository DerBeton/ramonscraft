<template>
    <div id="landing">
        <section id="landing-box">
            <img id="ramonscraft-logo" src="ramonscraft-shield-logo.svg" alt="Logo Ramonscraft">
            <!---<img id="ramon-rund" src="@/assets/img/ramon-rund.png" alt="Bild von Ramon">-->
            <h1 class="landing-heading">Ramon's <span class="h-craft">Craft</span></h1>
            <p>Zum alli mini verschiedene "Crafts" a eim Ort z'poste, han ich mir die Website baue. Es chömed immer wieder neui Inhalt und d'Siite selber befindet sich laufen im Wandel. Es lohnt
            sich also regelmässig drizluege!</br>
            Bi froge chamer mich gern <a class="contact-me-link" :href="prefix+decoded">kontaktiere</a>.</p>
            <svg @click="scrollDown" id="arrow-down" xmlns="http://www.w3.org/2000/svg" width="34.218" height="20.556" viewBox="0 0 34.218 20.556">
                <path id="Pfad_5" data-name="Pfad 5" d="M2159,826.52l16.527-18.383,16.2,18.383" transform="translate(2192.474 827.188) rotate(180)" fill="none" stroke="#048abf" stroke-width="2"/>
            </svg>
        </section>

    </div>

</template>

<script>
export default {
    data() {
        return {
            decoded: Buffer.from('bWFpbEByYW1vbnNjcmFmdC5jaA==', 'base64'),
            prefix: Buffer.from('bWFpbHRvOg==', 'base64')
        }
    },
    methods: {
        scrollDown() {

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
    height: 60vh;
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

#ramonscraft-logo {
    margin-bottom: 10px;
    margin: 20px;
    height: 260px;
}

.landing-heading {
    margin: 0;
    font-size: 60px;
    font-weight: bolder;
}

.h-craft {
    color: #048ABF;
}

p {
    font-size: 16px;
    font-weight: lighter;
    line-height: 1.4;
}

.contact-me-link {
    color: #333;
    text-decoration: none;
    box-shadow: inset 0 -2px 0 rgba(4,138,191,0.5), 0 1.5px 0 rgba(4,138,191,0.5);
    transition: box-shadow .4s;
    overflow: hidden;
}

.contact-me-link:hover {
    box-shadow: inset 0 -30px 0 rgba(4,138,191,0.5), 0 1.5px 0 rgba(4,138,191,0.5);
}

#arrow-down {
    margin-top: 30px;
    display: none;
    cursor: pointer;
}

@media only screen and (max-width: 620px) {
    .landing-heading {
        font-size: 46px;
    }
    #ramonscraft-logo {
        margin-top: 40px;
        height: 200px;
    }
}


/*
    #arrow-down {
        position: absolute;
        margin: 0 auto;
        padding: 20px;
        margin-bottom: 80px;
        bottom: 0;
        cursor: pointer;
    }
*/
</style>