<template>
  <section class="height-30 bg-dark text-white jarallax">
    
    <g-image
      src="~/resources/images/person-reading-burning-newspaper.jpg"
      class="jarallax-img opacity-60"
      alt="News"
    />
    <b-container>
      <b-row class="justify-content-center text-center">
        <b-col md="10" lg="8" class="pt-3 pb-3">
          <h1 class="display-4 mb-0">News</h1>
          <p class="lead">Ain't there always something strange happening?</p>
        </b-col>

        
      </b-row>
    </b-container>
  </section>
</template>

<script>
export default {
  props: [
    'totalCount'
  ]
}
</script>

