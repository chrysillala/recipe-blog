<template>
  <div class="post-list p-4 shadow-md transition duration-300 hover:shadow-lg">
    <g-link :to="post.path" class="grid md:grid-cols-6 gap-4">
      <g-image :src="post.image" :alt="post.title" class="md:col-span-2 rounded-lg" quality=85 />
      <div class="md:col-span-4">
        <h1 v-html ="post.title" class="text-xl font-bold" />
        <p v-html="post.description" class="text-base" />
        <div class="text-sm text-gray-800">
          <span>{{ post.date }}</span> - <span>{{ post.timeToRead }} minutes</span>
        </div>
      </div>
    </g-link>
  </div>
</template>

<script>
  export default {
    props: ["post"]
  }
</script>

<style scoped>

</style>