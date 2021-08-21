<template>
    <div id="blog">
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
                <b-col sm="12" md="6" class="d-flex my-auto">
                    <label class="description-text text-uppercase mr-2 my-auto">SORT BY DATE: {{sortByText}}</label>
                    <b-dropdown
                        dropright
                        size="sm"
                        menu-class="dd-menu"
                        toggle-class="dd-toggle"
                        variant="outline-info">
                        <b-dd-item-btn @click="onSortBy('asc')">Newest</b-dd-item-btn>
                        <b-dd-item-btn @click="onSortBy('desc')">Oldest</b-dd-item-btn>
                    </b-dropdown>
                </b-col>
                <b-col sm="12" md="6">
                    <b-input-group class="input-search-group w-75 float-md-right mt-3 mt-md-0">
                        <b-form-input
                            type="search"
                            class="bg-transparent border-right-0"
                            @input="onSearch"
                            debounce="500"
                            placeholder="Title search.." />
                        <b-input-group-append>
                            <b-input-group-text>
                                <b-icon icon="search" />
                            </b-input-group-text>
                        </b-input-group-append>
                    </b-input-group>
                </b-col>
            </b-row>
            <b-row v-if="articles.length" class="pt-5">
                <b-col class="d-flex flex-no-wrap flex-md-wrap justify-content-center justify-content-md-start">
                    <ArticleCard class="mr-4" v-for="article in articles" :key="article.slug" :article="article" />
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>

<script>
export default {
    data() {
        return {
            articles: [],
            sortByDirection: 'asc',
            searchText: '',
        }
    },
    async asyncData({ $content }) {
        const articles = await $content("blog")
            .only(['thumbnail', 'title', 'date'])
            .limit(10)
            .fetch();

        // console.log({articles});
        return {
            articles
        }
    },
    computed: {
        sortByText() {
            return this.sortByDirection === 'asc' ? 'Newest' : 'Oldest'
        }
    },
    methods: {
        async onSearch(value) {
            if(!value) {
                this.articles = await this.$content("blog")
                    .only(['thumbnail', 'title', 'date'])
                    .sortBy('date', this.sortByDirection)
                    .limit(10)
                    .fetch();
            }
            else {
                this.articles = await this.$content("blog")
                    .search('title', value)
                    .only(['thumbnail', 'title', 'date'])
                    .sortBy('date', this.sortByDirection)
                    .limit(10)
                    .fetch();
            }
        },
        onSortBy(value) {
            this.sortByDirection = value;
            this.onSearch();
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
        min-height: 100vh;
        padding-top: 120px;
        padding-bottom: 200px;
    }


</style>