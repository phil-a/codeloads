<template>
  <!--Waves Container-->
    <div>
      <svg class="waves" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" style="z-index: 999;"
      viewBox="0 24 150 28" preserveAspectRatio="none" shape-rendering="auto" transform="rotate(180, 0, 0)">
        <defs>
          <path id="gentle-wave" d="M-160 44c30 0 58-18 88-18s 58 18 88 18 58-18 88-18 58 18 88 18 v44h-352z" />
        </defs>
        <g class="parallax">
          <use xlink:href="#gentle-wave" x="48" y="0" fill="rgba(0,0,0,0.7" />
          <use xlink:href="#gentle-wave" x="48" y="3" fill="rgba(0,0,0,0.5)" />
          <use xlink:href="#gentle-wave" x="48" y="5" fill="rgba(0,0,0,0.3)" />
          <use xlink:href="#gentle-wave" x="48" y="7" fill="#2A2B2C" />
        </g>
      </svg>
    </div>
  <!--Waves end-->
</template>

