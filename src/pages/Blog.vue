<template>
  <Layout>
    <main>
      <h1>Blog</h1>

      <nav class="post">
        <g-link
          v-for="post in $page.allPost.edges"
          v-bind="post.node.id"
          :key="post.node.id"
          :to="
            '/blog/' +
              post.node.title
                .toLowerCase()
                .split(' ')
                .join('-')
          "
        >
          {{ post.node.title }}
        </g-link>
      </nav>
    </main>
  </Layout>
</template>

<page-query>
query {
    allPost{
        totalCount
        edges {
              node {
                id
                title
                author
                thumbnail
                date
                content
                timeToRead
            }
        }
    }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: "Blog",
  },
};
</script>

<style>
.post a {
  display: block;
}
</style>
