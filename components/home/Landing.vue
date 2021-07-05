<template>
    <div id="landing">
        <b-container id="landingContainer" fluid>
            <b-row>
                <b-col>
                    <p class="title-text">SPACE <br> WHERE IDEAS <br> MEET THE REALITY</p>
                </b-col>
            </b-row>
            <b-row>
                <b-col>
                    <p id="landingSubHeader">Custom web, mobile <br> and desktop development</p>
                </b-col>
            </b-row>
            <b-row>
                <b-col>
                    <b-button variant="outline-info" class="mr-2">GET A FREE QUOTE</b-button>
                    <b-button variant="outline-info">SCHEDULE A CALL</b-button>
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>

<style scoped>
    #landing {
        height: 100vh;
        width: 100%;
    }
    #landingContainer {
        position: relative;
        top: 15%;
    }
    #landingSubHeader {
        font-size: 2em;
        font-weight: normal;
        font-stretch: normal;
        font-style: normal;
        line-height: 1.17;
        letter-spacing: 0.54px;
        text-align: left;
        color: #ffffff;
        opacity: 0.7;
    }
</style>