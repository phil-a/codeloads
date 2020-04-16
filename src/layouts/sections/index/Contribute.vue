<template>
<div style="background-color: #3A3B3B;">
  <!-- <svg id="slit" xmlns="http://www.w3.org/2000/svg" version="1.1" width="100%" height="100" viewBox="0 0 100 100" preserveAspectRatio="none">
    <path id="slitPath2" d="M50 100 C49 80 47 0 40 0 L47 0 Z" />
    <path id="slitPath3" d="M50 100 C51 80 53 0 60 0 L53 0 Z" />
    <path id="slitPath1" d="M47 0 L50 100 L53 0 Z" />
  </svg> -->
  <section class="mt-5 text-center bg-gray-700 col-12 text-light ss-style-foldedcorner">
      <div class="container">
        <div class="row">
          <div class="col">
            <font-awesome class="mb-3" icon="sitemap" size="3x" />
            <h4 class="font-weight-light mb-3">Have you seen our list of recommended resources?</h4>
              <g-link
                class="btn btn-lg btn-primary"
                tabindex="-1"
                role="button"
                aria-disabled="true"
                to="/resources"
              >Check it out
              <font-awesome :icon="['fas', 'arrow-right']"></font-awesome>
              </g-link>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>