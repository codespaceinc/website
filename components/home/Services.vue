<template>
    <b-container fluid>
        <b-row>
            <b-col cols="12" md="6">
                <p class="title-text">WHO <br> WE ARE</p>
                <p class="description-text w-75">
                    Code Space Inc was founded in 2019 with a simple goal in mind: provide quality software development services and act as a trusted partner to startups, small and medium sized businesses.
                    We like what we do and take pride in the solutions we deliver to our customers. 
                </p>
            </b-col>
            <b-col cols="12" md="6">
                <b-row>
                    <b-col v-for="service in services" :key="service.name" cols="6">
                        <ServiceIcon v-bind="service" />
                    </b-col>
                </b-row>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
export default {
    data() {
        return {
            services: [
                { name: 'WEB', icon: 'services-web'},
                { name: 'MOBILE', icon: 'services-mobile'},
                { name: 'PC', icon: 'services-pc'},
                { name: 'UX/UI DESIGN', icon: 'services-uxui'},
                { name: 'BLOCKCHAIN', icon: 'services-blockchain'}
            ]
        }
    }
}
</script>
