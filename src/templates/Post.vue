<template>
  <Layout>
    <main>
      <h1 v-html="$page.post.title" />
      <h3>By {{ $page.post.author }} on {{ $page.post.date }}</h3>
      <g-image :src="$page.post.thumbnail" style="width: 10rem;" />
      <div v-html="$page.post.content" />
    </main>
    <Disqus shortname="blogportfolio" :identifier="$page.post.title" />
  </Layout>
</template>

<page-query>
query Post ($path: String!){
  post: post(path: $path){
    id
    title
    author
    thumbnail
    date
    content
    timeToRead
  }
}
</page-query>
