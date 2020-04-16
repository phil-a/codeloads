<template>
  <div>
    <div role="tablist" class="mb-5">
      <!-- <b-card no-body class="mb-1">
        <b-card-header header-tag="header" class="p-1" role="tab">
          <b-button block href="#" v-b-toggle.accordion-1 variant="dark"
            >Filter by Type</b-button
          >
        </b-card-header>
        <b-collapse
          id="accordion-1"
          accordion="my-accordion"
          role="tabpanel"
        >
          <b-card-body>
            <b-card-text>
              <ul class="ml-3 list-unstyled">
                <li>
                  <g-link :to="filterUrl('type', 'site')">Site</g-link>
                </li>
                <li>
                  <g-link :to="filterUrl('type', 'repository')"
                    >Repository</g-link
                  >
                </li>
              </ul>
            </b-card-text>
          </b-card-body>
        </b-collapse>
      </b-card> -->

      <b-card no-body class="mb-1">
        <b-card-header header-tag="header" class="p-1" role="tab">
          <b-button block href="#" v-b-toggle.accordion-2 variant="light"
            >Filter by Tag</b-button
          >
        </b-card-header>
        <b-collapse
          id="accordion-2"
          accordion="my-accordion"
          role="tabpanel"
          visible
        >
          <b-card-body>
            <b-card-text>
              <span v-for="tag in filterTags" :key="tag" class="badge-link">
                <b-badge
                  :to="filterUrl('tags', tag)"
                  variant="primary"
                  class="text-light"
                >
                  {{ tag }}
                </b-badge>
              </span>
              <g-link
                to="/resources"
                class="clear-icon float-right"
                active-class="no-active"
              >
                <font-awesome :icon="['fas', 'times-circle']"></font-awesome
                >&nbsp;
              </g-link>
            </b-card-text>
          </b-card-body>
        </b-collapse>
      </b-card>
    </div>
  </div>
</template>

<script>
import { each, uniq } from "lodash";

export default {
  methods: {
    filterUrl(type, value) {
      return `/resources/filter/${type}/${value}`;
    },
    noFilter() {
      return `/resources`;
    }
  },
  computed: {
    filterTags() {
      var tags = [];

      each(this.$static.resourceTags.edges, function(node) {
        each(node.node.tags, function(tag) {
          tags.push(tag.id);
        });
      });

      return uniq(tags);
    }
  }
};
</script>

<static-query>
  query {
    
    resourceTags : allResource {
      edges {
        node {
          tags { id }
        }
      }
    }
  }
</static-query>
