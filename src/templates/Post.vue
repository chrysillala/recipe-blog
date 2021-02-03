<template>
  <Layout>
    <h1 v-html="$page.post.title" />
    <g-image :src="$page.post.image" width="500" :alt="$page.post.title"/>
  	<article v-html="$page.post.content" />
  </Layout>
</template>

<script>
  export default {
    name: 'Post',
    metaInfo() {
      return {
        title: this.$page.post.title,
        meta: [
          { name: 'author', content: this.$page.post.title }
        ],
      }
    }
  }
</script>

<page-query>
query Post ($path: String!) {
  metadata {
    siteName
    siteDescription
  }
   post: post (path: $path) {
    id
    title
    content
    date (format: "D MMMM YYYY")
    timeToRead
    image
  }
}
</page-query>

<style scoped>

</style>