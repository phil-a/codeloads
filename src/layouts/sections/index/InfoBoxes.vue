<template>
  <div>

    <svg id="bigHalfCircle" xmlns="http://www.w3.org/2000/svg" version="1.1" width="100%" height="100" viewBox="0 0 100 100" preserveAspectRatio="none">
      <path d="M0 100 C40 0 60 0 100 100 Z"/>
    </svg>

    <section class="bg-primary">
      <b-container fluid>
        <b-row class="height-100 bg-primary">
          <b-col sm="12" md="12" lg="6" class="p-5" order="2" order-sm="1">
            <div class="text-center pb-5">
            <g-image
              class="d-md-none d-lg-none"
              src="~/resources/images/laptop.svg"
              width="256"
            />
            </div>
            <h3 class="display-4 text-center">Who are we?</h3>
            <div class="lead">
              We are software developers and tech enthusiasts out to change the world.
              <br />
              Our goal is to consistently learn (and teach) a little bit everyday, so that the rest of the world will pay it forward.
            </div>
            <div class="text-center">
              <g-link to="/pages/about-us" class="btn btn-lg btn-primary">Find out more</g-link>
            </div>
          </b-col>

          <b-col md="12" lg="6" order="1" order-sm="2" class="height-60 d-none d-sm-none d-md-block">
            <g-image
              class="bg-image "
              src="~/resources/images/laptop.svg"
              width="400"
              alt="Think different"
            />
          </b-col>
        </b-row> 
      </b-container>
    </section>

    <svg id="bigTriangleShadow" xmlns="http://www.w3.org/2000/svg" version="1.1" width="100%" height="100" viewBox="0 0 100 100" preserveAspectRatio="none">
			<path id="trianglePath1" d="M0 0 L50 100 L100 0 Z" />
			<path id="trianglePath2" d="M50 100 L100 40 L100 0 Z" />
		</svg>

  </div>
</template>