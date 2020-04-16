<template>
  <DefaultLayout>
    <!-- <SectionHeaderBanner></SectionHeaderBanner> -->
    <section class="pt-2 mb-5">
      <b-container>
        <b-row>
          <b-col cols="12" md="12" class="sidebar">
            <Sidebar></Sidebar>
          </b-col>
          <div class="resource-container">
            <ResourceCard
              v-for="edge in $page.records.edges"
              :key="edge.node.id"
              :record="edge.node"
              :data-image="`https://picsum.photos/240/320?random=${edge.node.id}`"
            />
          </div>
          <b-col>
            <Pagination
              :baseUrl="baseUrl(true, 'tags', $route.params.title)"
              :currentPage="$page.records.pageInfo.currentPage"
              :totalPages="$page.records.pageInfo.totalPages"
              :maxVisibleButtons="5"
              v-if="$page.records.pageInfo.totalPages > 1"
            />
          </b-col>
        </b-row>
      </b-container>
    </section>
    <SectionContribute></SectionContribute>
  </DefaultLayout>
</template>

<script src="~/pageScripts/resources.js"></script>

<page-query>
  query($title: [String], $page:Int) {
    records: allResource(filter:{tags:{contains:$title}},sortBy:"createdAt", order:DESC, perPage: 9, page: $page) @paginate {
      totalCount
      pageInfo {
        totalPages
        currentPage
      }
      edges {
        node {
          id,
          title, 
          link,
          excerpt,
          tags {
              title,
              path
          }
        }
      }
    }
  }
</page-query>
