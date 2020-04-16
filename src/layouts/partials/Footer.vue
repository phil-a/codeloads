<template>
  <footer class="bg-gray-800">
			<svg id="curveDownColor" xmlns="http://www.w3.org/2000/svg" version="1.1" width="100%" height="100" viewBox="0 0 100 100" preserveAspectRatio="none">
				<path d="M0 0 C 50 100 80 100 100 0 Z"/>
			</svg>
    <b-container>
      <b-row align-h="between" align-v="center">
        <b-col cols="auto">
          <ul class="list-inline mb-0">
            <li class="list-inline-item mb-0">
              <b-navbar-brand class="mb-0">
                <g-link to="/" class="nav-link text-white">
                  <font-awesome :icon="['fas', 'keyboard']"></font-awesome>
                  {{ $static.metadata.siteName }}
                </g-link>
              </b-navbar-brand>
            </li>

          </ul>
        </b-col>
        <b-col cols="auto" class="text-sm-right">
          <ul class="list-inline mb-0">
            <li class="list-inline-item mb-0">
              
                <g-link to="/pages/about-us" class="nav-link">
                  About Us
                </g-link>
              
            </li>
            <li class="list-inline-item mb-0">
              
              <g-link to="/pages/contribute" class="nav-link">
                Contribute
              </g-link>
              
            </li>
            <li class="list-inline-item mb-0">
              
                <g-link to="/credits" class="nav-link">
                  Credits
                </g-link>
              
            </li>
            <li class="list-inline-item mb-0">
              <b-navbar-brand class="mb-0">
              <a href="https://github.com/phil-a/codeloads" target="_blank" class="nav-link text-light" alt="Codeloads Github Repository" rel="noopener">
                <font-awesome :icon="['fab', 'github']"></font-awesome>
              </a>
              </b-navbar-brand>
            </li>
          </ul>
        </b-col>
      </b-row>
      <b-row>
        <b-col>
          <div class="copyright ml-3">Copyright {{ new Date().getFullYear() }}. All rights reserved.</div>
        </b-col>
      </b-row>
    </b-container>
  </footer>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>