<template>
  <Layout>

    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <!-- <g-image alt="Example image" src="~/favicon.png" width="135" /> -->
    <header class="text-center">
      <h1 class="text-4xl md:text-5xl mb-4 text-blue-700 font-bold uppercase">🍜 Markisak 🍛</h1>
      <h2 class="text-3xl mb-4" v-text="$page.metadata.siteDescription"></h2>
    </header>

    <section class="posts grid row-gap-6">
      <PostList v-for="edge in $page.allPost.edges" :key="edge.node.id" :post="edge.node" />
    </section>

    <section class="mt-8">
      <p>Total Posts: <span v-text="$page.allPost.totalCount"></span></p>
    </section>
  </Layout>
</template>

<script>
import PostList from '@/components/PostList.vue';
export default {
  components: {
    PostList,
  },
  metaInfo: {
    title: '🍜 Markisak 🍛'
  }
}
</script>

<page-query>
query {
  metadata {
    siteName
    siteDescription
  }
  allPost(filter: { active: { eq: true }}) {
    totalCount
    edges {
      node {
        id
        title
        timeToRead
        description
        date (format: "D MMMM YYYY")
        path
        image
      }
    }
  }
}
</page-query>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
