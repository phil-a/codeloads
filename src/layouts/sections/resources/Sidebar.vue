<template>
  <div>
    <div role="tablist" class="mb-5">
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
                  :variant="selected==tag ? 'primary' : 'light'"
                  :class="selected==tag ? 'text-light' : 'text-dark'"
                >
                  {{ tag }}
                </b-badge>
              </span>
              <g-link
                v-if="selected"
                to="/resources"
                class="link float-right"
                active-class="no-active"
              >
                Remove Filter
                &nbsp;
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
  props: ['selected'],
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
          tags { id, title }
        }
      }
    }
  }
</static-query>
