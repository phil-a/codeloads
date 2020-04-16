<template>
  <DefaultLayout>
    
    <SectionHeader :record="$page.entry"></SectionHeader>

    <b-container class="mt-5 mb-5">
      <b-row>
        <b-col order="2" order-lg="1" cols="12" lg="8" class="article-content">
          <div v-html="$page.entry.content" />
        </b-col>
        <b-col lg="3" order="1" order-lg="2" offset-lg="1" class>
          <SectionSidebar :record="$page.entry"></SectionSidebar>
        </b-col>
      </b-row>
    </b-container>

    
      <svg id="clouds" xmlns="http://www.w3.org/2000/svg" version="1.1" width="100%" height="100" viewBox="0 0 100 100" preserveAspectRatio="none">
				<path d="M-5 100 Q 0 20 5 100 Z
						 M0 100 Q 5 0 10 100
						 M5 100 Q 10 30 15 100
						 M10 100 Q 15 10 20 100
						 M15 100 Q 20 30 25 100
						 M20 100 Q 25 -10 30 100
						 M25 100 Q 30 10 35 100
						 M30 100 Q 35 30 40 100
						 M35 100 Q 40 10 45 100
						 M40 100 Q 45 50 50 100
						 M45 100 Q 50 20 55 100
						 M50 100 Q 55 40 60 100
						 M55 100 Q 60 60 65 100
						 M60 100 Q 65 50 70 100
						 M65 100 Q 70 20 75 100
						 M70 100 Q 75 45 80 100
						 M75 100 Q 80 30 85 100
						 M80 100 Q 85 20 90 100
						 M85 100 Q 90 50 95 100
						 M90 100 Q 95 25 100 100
						 M95 100 Q 100 15 105 100 Z">
				</path>
			</svg>
      
      <b-row class="text-center pt-5 bg-white">
        <b-col>
          <h2 class="display-4">You might also like</h2>
        </b-col>
      </b-row>

      <b-row class="height-30 bg-white-to-cloud pb-5 related-records">
        
        <b-col sm="12" md="6" class="pr-5 pl-5 mt-5 border-right" v-for="relatedRecord in relatedRecords" :key="relatedRecord.node.id">
          <h4 class="">{{ relatedRecord.node.title }}</h4>
          <p v-html="relatedRecord.node.excerpt"></p>

          <g-link :to="recordLink(relatedRecord.node)" class="btn btn-lg btn-primary">Continue reading</g-link>
          
        </b-col>
        
      </b-row>
    
  </DefaultLayout>
</template>

<page-query>
  query Article($recordId: ID!, $tags: [String]) {
    entry : article(id: $recordId) {
      title
      content
      excerpt
      createdAt(format:"Do MMMM YYYY")
      timeToRead
      tags {
          title
          path
      },
      headings {
        depth
        value
        anchor
      },
    }

    related: allArticle(
      filter: { id: { ne: $recordId }, tags: {containsAny: $tags} }
    ) {
      edges {
        node {
          id
          title
          excerpt
          slug
        }
      }
    }

    
  }
</page-query>

<script>
import SectionHeader from "~/layouts/sections/article/HeaderBanner.vue";
import SectionSidebar from "~/layouts/sections/article/Sidebar.vue";
import { sampleSize } from "lodash";
export default {
  components: {
    SectionHeader,
    SectionSidebar
  },

  methods: {
    recordLink(record) {      
      return `/articles/${record.slug}`;
    }
  },

  computed: {
    relatedRecords() {
      return sampleSize(this.$page.related.edges, 2);
    },
  },

  metaInfo() {
    return {
      title: this.$page.entry.title
    };
  }
};
</script>

<style>
@import "https://github.githubassets.com/assets/gist-embed-d89dc96f3ab6372bb73ee45cafdd0711.css";
</style>