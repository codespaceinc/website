<template>
      <b-card
        :img-src="article.thumbnail"
        :img-alt="article.name"
        img-top
        tag="article"
        class="article-card mb-4">
        <div v-if="article.tags" class="mb-1">
            <b-badge v-for="tag in article.tags" :key="tag" variant="info" class="bg-transparent mr-1 px-2 text-capitalize text-primary border border-info font-weight-normal">{{tag}}</b-badge>
        </div>

        <b-card-title class="text-primary text-uppercase">
            {{ article.title }}
        </b-card-title>

        <b-card-sub-title>
            {{ new Date(article.date).toDateString() }}
        </b-card-sub-title>

        <b-card-text class="pt-2">
            {{ article.preview }}
        </b-card-text>

        <b-card-footer class="p-0">
            <b-button :to="article.path" variant="outline-primary">Read More</b-button>
        </b-card-footer>
  </b-card>
</template>

<script>
export default {
    props: {
        article: Object
    }
}
</script>

<style lang="scss">
    .article-card {
        min-height: 400px;
        padding: 15px;
        border: 1px solid #808080;
        border-radius: 10px;
        background-color: rgba(0,0,0,0.6);
        img {
            height: 200px;
        }
    }
</style>