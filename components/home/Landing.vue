<template>
        <b-container id="landingContainer" fluid class="d-flex flex-column">
            <b-row>
                <b-col>
                    <p class="title-text">SPACE <br> WHERE IDEAS <br> MEET THE REALITY</p>
                </b-col>
            </b-row>
            <b-row>
                <b-col>
                    <p id="landingSubHeader" class="description-text">Custom web, mobile <br> and desktop development</p>
                </b-col>
            </b-row>
            <b-row>
                <b-col>
                    <b-button class="p-2 mr-2" href="#contact" variant="outline-primary"><span :class="[videoPaused && 'get-quote']">GET A FREE QUOTE</span></b-button>
                    <b-button class="p-2" href="https://calendly.com/codespaceinc/discovery-call" target="_blank" variant="outline-primary">SCHEDULE A CALL</b-button>
                </b-col>
            </b-row>
        </b-container>
</template>

<script>
export default {
    props: {
        videoPaused: Boolean
    }
}
</script>

<style scoped>

    @import url("~/assets/css/flickering.css");

    .get-quote {
        animation: text-flicker 3s linear infinite;
    }

    .get-quote-flicker {
        animation: border-flicker 2s linear infinite;
    }

    #landingContainer {
        height: 100vh;
        position: relative;
        top: 15%;
    }
    #landingSubHeader {
        font-size: 2em;
        line-height: 1;
        color: white;
    }
</style>