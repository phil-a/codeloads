<template>
<b-col class="py-2" lg="6" md="6" sm="12"> 
<div class="card-link-container"
    v-on:mouseover="mouseover"
    v-on:mouseleave="mouseleave">
  <g-link class="card-link" :to="recordLink">
    <article :class="blogCardClass">
      <img v-if="indexEven" class="post-image" src='https://s3-us-west-2.amazonaws.com/s.cdpn.io/1159990/pike-place.jpg' />
      <div class="article-details">
        <h4 class="post-category">{{ record.createdAt }} </h4>
        <h3 class="post-title">{{record.title}}</h3>
        <p class="post-description">{{record.excerpt}}</p>
        <p class="post-author"><span class="small"><strong>&#183;</strong> {{ record.timeToRead }} min read</span></p>
      </div>
      <img v-if="!indexEven" class="post-image" src='https://s3-us-west-2.amazonaws.com/s.cdpn.io/1159990/pike-place.jpg' />
    </article>
  </g-link>
</div>
<div v-on:mouseover="mouseover"
    v-on:mouseleave="mouseleave" 
    :class="tagCardClass">
    <div class="tag-details">
      <span class="badge-link" v-for="tag in record.tags" :key="tag.title">
      <g-link :to="tag.path" variant="light">
        <b-badge variant="primary">#{{ tag.title }}</b-badge>
      </g-link>
    </span>
    </div>
</div>
</b-col>
</template>

<script>

export default {
  components: {
  },
  data() {
    return {
      tagCardClass: "tag-card hide",
    }
  },
  props: ['record', 'index'],
  computed: {
    blogCardClass() {
      return this.indexEven ? 'blog-card left-image' : 'blog-card right-image';
    },
    indexEven() {
      return this.index % 2 == 0;
    },
    recordLink() {
      if( this.record.recordType == 'Article') {
        return `/articles/${this.record.slug}`;
      }
      if( this.record.recordType == 'News') {
        return `/news/${this.record.slug}`;
      }

      return this.record.path;
    }
  },
  methods: {
    mouseover: function(){
      this.tagCardClass= 'tag-card'
    },    
    mouseleave: function(){
      this.tagCardClass = 'tag-card hide'
    }
  }
}
</script>