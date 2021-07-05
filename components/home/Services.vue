<template>
    <b-container>
        <b-row>
            <b-col cols="6">
                <p class="title-text">WHO <br> WE ARE</p>
                <p class="subtitle-text w-75">
                    There will be some text that talks a little more about the company and then we should explain what company does via visual storytelling. I really like how Apple does it with bit pictures and big fonts by the way but maybe this style is not appropriate here ? Maybe have a slideshow or something with astronaut using all 3 types of platforms we offer software development services for:
                </p>
            </b-col>
            <b-col cols="6">
                <b-container fluid>
                    <b-row>
                        <b-col v-for="service in services" :key="service" cols="6">
                            <ServiceIcon :name="service" />
                        </b-col>
                    </b-row>
                </b-container>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
export default {
    data() {
        return {
            services: [
                'WEB',
                'MOBILE',
                'PC',
                'UX/UI DESIGN',
                'BLOCKCHAIN'
            ]
        }
    }
}
</script>
