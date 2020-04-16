<template>
  <DefaultLayout>
    
    <SectionHeaderBanner></SectionHeaderBanner>

    <SectionLatestArticles></SectionLatestArticles>

    <SectionContribute></SectionContribute>

    <SectionLatestNews></SectionLatestNews>

    <SectionInfoBoxes></SectionInfoBoxes>

    <SectionOpenSource></SectionOpenSource>
       
  </DefaultLayout>
</template>

<script>
import SectionHeaderBanner from "~/layouts/sections/index/HeaderBanner.vue";
import SectionLatestArticles from "~/layouts/sections/index/LatestArticles.vue";
import SectionLatestNews from "~/layouts/sections/index/LatestNews.vue";

import SectionContribute from "~/layouts/sections/index/Contribute.vue";
import SectionInfoBoxes from "~/layouts/sections/index/InfoBoxes.vue";
import SectionOpenSource from "~/layouts/sections/index/OpenSource.vue";

export default {
  components: {
    SectionHeaderBanner,
    SectionLatestArticles,
    SectionLatestNews,
    SectionContribute,
    SectionInfoBoxes,
    SectionOpenSource
  },
  metaInfo: {
    title: "Home"
  }
};
</script>

