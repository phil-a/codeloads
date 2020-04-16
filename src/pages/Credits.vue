<template>
  <DefaultLayout>
    <SectionHeaderBanner></SectionHeaderBanner>
    <section class="section pt-5">
      <b-container>
        <b-row>
          <div class="resource-container">
            <ResourceCard v-for="edge in $page.records.edges" :key="edge.node.id" :record="edge.node" :data-image="`https://picsum.photos/240/320?random=${edge.node.id}`" />
          </div>
        </b-row>
      </b-container>
    </section>
    <SectionContribute></SectionContribute>
  </DefaultLayout>
</template>

<script>
import ResourceCard from "~/components/ResourceCard.vue";
import SectionContribute from "~/layouts/sections/credits/Contribute.vue";
import SectionHeaderBanner from "~/layouts/sections/credits/HeaderBanner.vue";

export default {
  components: {
    ResourceCard,
    SectionContribute,
    SectionHeaderBanner
  },

  metaInfo: {
    title: "Credit Due"
  }
};
</script>

<page-query>
  query {
    records: allCredits {
      edges {
        node {
          id,
          title, 
          link,
          content
        }
      }
    }
  }
</page-query>