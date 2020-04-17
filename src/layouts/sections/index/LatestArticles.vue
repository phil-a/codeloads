<template>
  <section class="pt-5">
    <b-container>
      <div class="text-center">
        <h2>Latest Articles</h2>
        <div class="lead">Curious what new articles are on our website? Check out our latest articles!</div>
      </div>

      <div class="container article-container">
        <b-row>
          <RecordCard
            v-for="edge in $static.records.edges"
            :key="edge.node.id"
            :record="edge.node"
          />
        </b-row>
      </div>
    </b-container>
    <g-link to="/articles" class="btn btn-lg btn-primary mt-5">
      Browse all articles
      <font-awesome :icon="['fas', 'arrow-right']"></font-awesome>
    </g-link>
  </section>
</template>

<script>
import RecordCard from "~/components/RecordCard.vue";

export default {
  components: {
    RecordCard
  }
};
</script>

<static-query>
  query {
    records: allArticle(limit:6, sortBy:"createdAt") {
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