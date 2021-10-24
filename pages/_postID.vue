<template>
  <div>
    <h1>{{ post.title }}</h1>
    <p>{{ post.body }}</p>
    <NuxtLink to="/">Back to home</NuxtLink>
  </div>
</template>
<script>
export default {
  async asyncData({ params, redirect }) {
    const posts = await fetch(
      'https://jsonplaceholder.typicode.com/posts'
    ).then((res) => res.json())

    const filteredPosts = posts.find(
      (el) => el.id == params.postID
    )
    if (filteredPosts) {
      return { post: filteredPosts }
    } else {
      redirect('/')
    }
  }
}
</script>
