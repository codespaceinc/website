<template>
<div id="article">
  <b-container id="container">
    <b-row class="mb-1">
      <b-col>
        <b-link
          class="text-decoration-none text-primary"
          @click="$router.back()" 
          @mouseenter="backArrowIcon='arrow-left-circle-fill'" 
          @mouseleave="backArrowIcon='arrow-left-circle'">
          <h4>
            <b-icon :icon="backArrowIcon" class="mr-2"></b-icon>Go Back
          </h4>
        </b-link>
      </b-col>
      <b-col>
        <div class="float-right">
          <h4 class="d-inline text-primary mr-1"><b-icon icon="share" /></h4>
          <ShareNetwork
            class="text-decoration-none"
            network="facebook"
            :url="$route.query.page"
            :title="post.title"
            description="This week, I’d like to introduce you to 'Vite', which means 'Fast'. It’s a brand new development setup created by Evan You."
            >
              <h4 class="d-inline bg-fb py-1 px-2 text-light rounded">
                <b-icon class="" icon="facebook" />
              </h4>
            </ShareNetwork>
            <ShareNetwork
            class="text-decoration-none"
            network="linkedin"
            :url="$route.query.page"
            :title="post.title"
            >
              <h4 class="d-inline bg-linkedin py-1 px-2 text-light rounded">
                <b-icon icon="linkedin" />
              </h4>
            </ShareNetwork>
        </div>
      </b-col>
    </b-row>
    <b-row>
      <b-col>
        <article class="p-3">
          <div class="text-center mb-3">
            <p class="title-text text-break">{{ post.title }}</p>
            <img id="thumbnail" :src="post.thumbnail" alt="thumbnail" />
          </div>
          <nuxt-content :document="post" />
        </article>
      </b-col>
    </b-row>
  </b-container>
  
</div>
</template>

<script>
export default {
  data() {
    return {
      backArrowIcon: 'arrow-left-circle'
    }
  },
  async asyncData({ $content, params, error }) {
    let post;
    try {
      post = await $content("blog", params.slug).fetch();
      // OR const article = await $content(`articles/${params.slug}`).fetch()
      // console.log(post.thumbnail);
    } catch (e) {
      error({ message: "Blog Post not found" });
    }

    return {
      post,
    };
  },
};
</script>

<style lang="scss">
  #container {
    min-height: 100vh;
    padding-top: 120px;
    padding-bottom: 200px;
  }

  #article {
    background-image: url("~/assets/images/bg-lg.webp");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    background-color: #040004;
  }

  article {
    border: 1px solid #808080;
    border-radius: 10px;
    background-color: rgba(0,0,0,0.3);
  }

  #thumbnail {
    object-fit: contain;
  }
  
  .nuxt-content {
    img {
      height: 100%;
      width: 100%;
      object-fit: contain;
    }
  }

</style>