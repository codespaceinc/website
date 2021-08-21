<template>
    <b-container fluid>
        <b-row>
            <b-col cols="12" md="3" class="my-auto">
                <span id="ourProcess">OUR PROCESS</span>
            </b-col>
            <b-col cols="12" md="9">
                <b-row class="pb-3">
                    <b-col cols="6">
                        <p class="our-process-step space-blue">01</p>
                        <span class="step-title">Inquiry received.</span><br>
                        <span class="description-text"> We'll schedule a discovery call within the next 2 business days</span>
                        <!-- <span id="start-circle"></span> -->
                    </b-col>
                    <b-col cols="6">
                        <p class="our-process-step space-blue">02</p>
                        <span class="step-title">Discovery call.</span><br>
                        <span class="description-text">We'll introduce ourselves and gather more details about your project</span>
                    </b-col>
                </b-row>
                <b-row class="border-03-04 pb-3">
                    <b-col cols="6">
                        <p class="our-process-step space-blue">03</p>
                        <span class="step-title">Requirements analysis.</span><br>
                        <span class="description-text">We'll meet with the team to discuss your project and come up with an estimate</span>
                    </b-col>
                    <b-col cols="6">
                        <p class="our-process-step space-blue">04</p>
                        <span class="step-title">Proposal.</span><br>
                        <span class="description-text">We'll send you a proposal with estimated hours and project cost</span>
                    </b-col>
                </b-row>
                <b-row class="border-05-06 pb-3">
                    <b-col cols="6">
                        <p class="our-process-step space-blue">05</p>
                        <span class="step-title">Work begins.</span><br>
                        <span class="description-text">We assign a team consisting of developers, QAs and a project manager to work on your idea.</span>
                    </b-col>
                    <b-col cols="6">
                        <p class="our-process-step space-blue">06</p>
                        <span class="step-title">Handoff.</span><br>
                        <span class="description-text">After a few iterations of change requests and testing we release the complete application</span>
                    </b-col>
                </b-row>
            </b-col>
        </b-row>
    </b-container>
</template>

<style scoped>
    #ourProcess {
        font-size: 5em;
        font-weight: bold;  
        padding-top: 10px;
        cursor: default;
        line-height: 1;
    }

    .our-process-step {
        font-size: 7em;
        font-weight: 600;
        line-height: 1;
        letter-spacing: 2.39px;
        cursor: default;
    }

    .step-title {
        color: white;
        font-weight: bold;
        opacity: 1 !important;
    }

    .border-03-04 {
        border-top: 1px solid rgba(255,255,255,0.2);
        border-right: 1px solid rgba(255,255,255, 0.2);
        border-bottom: 1px solid rgba(255,255,255, 0.5);
    }
    .border-05-06 {
        border-left: 1px solid rgba(255,255,255, 0.2);
        border-bottom: 1px solid rgba(255,255,255, 0.5);
    }

    @media only screen and (min-width: 768px) {
        #ourProcess {
            border-top: 1px solid var(--space-blue);
            font-size: 7em;
            writing-mode: vertical-lr;
        }
    }

</style>