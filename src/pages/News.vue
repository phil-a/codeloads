<template>
  <DefaultLayout>
    <SectionHeaderBanner :totalCount="$page.records.totalCount"></SectionHeaderBanner>
    <section class="col-12 pt-5 ss-style-roundedsplit">
      <b-container class="pb-5">
        <div class="container news-container">
          <b-row>
            <BlogCard 
              v-for="(edge, index) in $page.records.edges"
              :key="edge.node.id"
              :record="edge.node"
              :index="index" />
          </b-row>
        </div>
      </b-container>

      <Pagination
        baseUrl="/news"
        :currentPage="$page.records.pageInfo.currentPage"
        :totalPages="$page.records.pageInfo.totalPages"
        :maxVisibleButtons="5"
        v-if="$page.records.pageInfo.totalPages > 1"
      />
    </section>
  </DefaultLayout>
</template>

<script>
import BlogCard from "~/components/BlogCard.vue";
import Pagination from "~/components/Pagination.vue";
import SectionHeaderBanner from "~/layouts/sections/news/HeaderBanner.vue";

export default {
  components: {
    BlogCard,
    Pagination,
    SectionHeaderBanner
  },
  metaInfo() {
    return {
      title: `Browse all news`
    };
  }
};
</script>

<page-query>
  query ($page: Int) {
    records: allNews(perPage: 9, page: $page) @paginate {
      totalCount
      pageInfo {
        totalPages
        currentPage
      }
      edges {
        node {
          recordType
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
</page-query>
