<template>
  <section class="pt-5">
    <b-container>
      <div class="text-center">
        <h2>Latest News</h2>
      </div>

      <div class="container news-container">
        <b-row>
            <BlogCard 
              v-for="(edge, index) in $static.records.edges"
              :key="edge.node.id"
              :record="edge.node"
              :index="index" />
        </b-row>
      </div>
      <g-link to="/news" class="btn btn-lg btn-primary mt-5">Browse all news <font-awesome :icon="['fas', 'arrow-right']"></font-awesome></g-link>
    </b-container>
  </section>
</template>

<script>
import BlogCard from "~/components/BlogCard.vue";

export default {
  components: {
    BlogCard
  }
};
</script>

<static-query>
  query {
    records: allNews(limit:3, sortBy:"createdAt") {
      edges {
        node {
          title, 
          path,
          slug,
          excerpt,
          createdAt(format:"Do MMMM YYYY"),
          timeToRead,
          tags {
            title,
            path
          }
        }
      }
    }
  }
</static-query>