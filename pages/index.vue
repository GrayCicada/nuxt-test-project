<template>
<div>
  <h1>Пупа привет</h1>
  <ul v-for="post in posts" :key="post.id">
    <NuxtLink :to="`/${post.id}`">
      <li>{{ post.title }}</li>
    </NuxtLink>
  </ul>
</div>
</template>

<script>
export default {
  async asyncData() {
    const posts = await fetch('https://jsonplaceholder.typicode.com/posts')
    .then((res) => res.json())

    return { posts }
  }
}
</script>
