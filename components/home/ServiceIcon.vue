<template>
    <div class="my-3 text-center">
        <b-img-lazy width="64px" height="64px" :src="`icons/${icon}.svg`" :alt="`${name} service icon`" />
        <h5 class="pt-3 space-blue">{{name}}</h5>
        <!-- <p class="description-text">Description</p> -->
    </div>
</template>

<script>
export default {
    props: {
        name: String,
        icon: String
    },
    computed: {
        iconPath() {
            return "@/assets/images/logo.png";
        }
    }
}
</script>
