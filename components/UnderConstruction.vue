<template>
    <div id="blur" class="d-flex justify-content-center align-items-center">
            <div>
                <p class="title-text">UNDER CONSTRUCTION</p>
                <b-progress :value="60" variant="info" striped animated></b-progress>
            </div>
        </div>
</template>

<style>
    #blur {
        height: 100vh;
        background: rgba(0, 0, 0, 0.2);
        backdrop-filter: blur(8px);
    }
</style>