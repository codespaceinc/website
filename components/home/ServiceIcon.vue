<template>
    <div>
        <img width="64px" height="64px" src="~/assets/images/logo.png" alt="service icon" />
        <h5 class="pt-3 space-blue">{{name}}</h5>
        <p class="description-text">Description</p>
    </div>
</template>

<script>
export default {
    props: {
        name: String
    }
}
</script>
