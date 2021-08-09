<template>
      <b-card
        :img-src="article.img || 'https://picsum.photos/600/300/?image=25'"
        img-alt="Image"
        img-top
        tag="article"
        style="max-width: 20rem;"
        class="article-card">
        <div class="mb-1">
            <b-badge v-for="tag in article.tags" :key="tag" variant="info" class="bg-transparent mr-1 px-2 text-capitalize space-blue space-blue-border">{{tag}}</b-badge>
        </div>

        <b-card-title class="space-blue text-uppercase">
            {{ article.title }}
        </b-card-title>

        <b-card-sub-title>
            {{ article.date.toDateString() }}
        </b-card-sub-title>

        <b-card-text class="pt-2">
            {{article.preview}}
        </b-card-text>

        <b-card-footer class="p-0">
            <b-button  :href="`articles/${article.id}`" variant="outline-info">Read More</b-button>
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
        padding: 10px;
        border: 1px solid #808080;
        border-radius: 10px;
        background-color: rgba(0,0,0,0.5);
    }
</style>