<template>
    <div id="blog">
        <b-container id="container">
            <b-row>
                <b-col>
                    <h1 class="title-text">Space Blog</h1>
                </b-col>
            </b-row>
            <b-row class="pt-3">
                <b-col>
                    <b-button :class="['mr-2', articlesFilter === 'all' && 'active-btn']" variant="outline-primary" @click="articlesFilter = 'all'">All</b-button>
                    <b-button :class="['mr-2', articlesFilter === 'article' && 'active-btn']" variant="outline-primary" @click="articlesFilter = 'article'">Articles</b-button>
                    <b-button :class="['mr-2', articlesFilter === 'guide' && 'active-btn']" variant="outline-primary" @click="articlesFilter = 'guide'">Guides</b-button>
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
                        variant="outline-primary">
                        <b-dd-item-btn @click="onSortBy('desc')">Newest</b-dd-item-btn>
                        <b-dd-item-btn @click="onSortBy('asc')">Oldest</b-dd-item-btn>
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
            <b-row v-if="displayedArticles.length" class="pt-5">
                <b-col sm="1" md="4" lg="3" v-for="article in displayedArticles" :key="article.slug">
                    <ArticleCard :article="article" />
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
            sortByDirection: 'desc',
            searchText: '',
            articlesFilter: 'all'
        }
    },
    async asyncData({ $content }) {
        const articles = await $content("blog")
            .only(['thumbnail', 'title', 'date', 'tags'])
            // .limit(10)
            .fetch();

        // console.log({articles});
        return {
            articles
        }
    },
    computed: {
        sortByText() {
            return this.sortByDirection === 'asc' ? 'Oldest' : 'Newest'
        },
        displayedArticles() {
            return this.articlesFilter === 'all'
                ? this.articles
                : this.articles.filter(a => a.tags.includes(this.articlesFilter));
        }
    },
    methods: {
        async onSearch(value) {
            if(!value) {
                this.articles = await this.$content("blog")
                    .only(['thumbnail', 'title', 'date', 'tags'])
                    .sortBy('date', this.sortByDirection)
                    // .limit(10)
                    .fetch();
            }
            else {
                this.articles = await this.$content("blog")
                    .search('title', value)
                    .only(['thumbnail', 'title', 'date', 'tags'])
                    .sortBy('date', this.sortByDirection)
                    // .limit(10)
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

<style lang="scss" scoped>
    #blog {
        background-image: url("~/assets/images/bg-lg.webp");
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
        background-color: #040004;
    }

    #container {
        min-height: 100vh;
        padding-top: 120px;
        padding-bottom: 200px;
    }


</style>