<template>
    <div id="blog">
        <!-- <UnderConstruction /> -->
        <b-container id="blogContainer">
            <b-row>
                <b-col>
                    <h1 class="title-text">Space Blog</h1>
                </b-col>
            </b-row>
            <b-row class="pt-3">
                <b-col>
                    <b-button class="mr-2" variant="outline-info">All</b-button>
                    <b-button class="mr-2" variant="outline-info">Articles</b-button>
                    <b-button variant="outline-info">Guides</b-button>
                </b-col>
            </b-row>
            <b-row class="pt-3">
                <b-col cols="6" class="d-flex my-auto">
                    <label class="description-text text-uppercase mr-2 my-auto">SORT BY DATE: {{sortBy}}</label>
                    <b-dropdown
                        dropright
                        size="sm"
                        menu-class="dd-menu"
                        split-class="dd-split"
                        variant="outline-info">
                        <b-dd-item link-class="space-blue">Newest</b-dd-item>
                        <b-dd-item link-class="space-blue">Oldest</b-dd-item>
                    </b-dropdown>
                </b-col>
                <b-col cols="6" class="clearfix">
                    <b-input
                        id="articleSearch"
                        type="search"
                        class="bg-transparent float-right w-50"
                        @input="onSearch"
                        placeholder="Search" />
                </b-col>
            </b-row>
            <b-row class="pt-5">
                <b-col class="d-flex flex-row flex-wrap">
                    <ArticleCard class="mr-4" v-for="article in articles" :key="article.id" :article="article" />
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>

<script>
export default {
    data() {
        return {
            sortBy: 'Newest',
            allArticles: [
                {
                    id: 1,
                    date: new Date(),
                    title: 'Blog Post #1',
                    tags: ['article', 'howto'],
                    preview: 'Custom, web, mobile and desktop development, Custom, web, mobile and desktop development, Custom, web, mobile and desktop development.'
                },
                {
                    id: 2,
                    date: new Date(),
                    title: 'Blog Post #2',
                    tags: ['howto'],
                    preview: 'Custom, web, mobile and desktop development, Custom, web, mobile and desktop development, Custom, web, mobile and desktop development.'
                }
            ],
            searchText: '',
        }
    },
    beforeMount() {
        this.$content("blog").fetch().then(posts => console.log(posts));
    },
    computed: {
        articles() {
            return this.allArticles.filter(a => a.title.toUpperCase().includes(this.searchText.toUpperCase()))
        }
    },
    methods: {
        onSearch(value) {
            this.searchText = value;
        }
    }
}
</script>

<style lang="scss">
    #blog {
        background-image: url("~/assets/images/bg-lg.webp");
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
        background-color: #040004;
    }

    #blogContainer {
        padding-top: 120px;
        padding-bottom: 200px;
    }


</style>