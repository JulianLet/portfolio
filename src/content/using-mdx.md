---
title: 'Using MDX'
description: 'Lorem ipsum dolor sit amet'
pubDate: 'Jun 01 2022'
heroImage: '/src/assets/blog-placeholder-1.jpg'
---

<Image src="/src/assets/02_Shadertoy/light-test.jpg" alt="Light test" width={400} height={300} />
<img src="/src/assets/02_Shadertoy/animated-shader.gif" alt="Animated shader" width="400" />

<!-- center image -->
<div class="center">
  <Image src="/src/assets/02_Shadertoy/light-test.jpg" alt="Light test" width={400} height={300} />
</div>

<style>
.center {
  text-align: center; /* horizontally centers inline elements like img */
}
.center img {
  display: inline-block; /* ensures image respects centering */
}
</style>

<!-- gallery -->
<div class="gallery">
  <img src="/src/assets/02_Shadertoy/light-test.jpg" alt="Light test" width="200" />
  <img src="/src/assets/02_Shadertoy/animated-shader.gif" alt="Animated shader" width="200" />
  <img src="/src/assets/02_Shadertoy/shadow-test.jpg" alt="Shadow test" width="200" />
</div>

<style>
.gallery {
  display: flex;
  gap: 1rem; /* space between images */
  justify-content: center; /* center the row */
  flex-wrap: wrap; /* wrap to next line if small screen */
}
</style>

<!-- grid -->
<div class="grid-gallery">
  <img src="/src/assets/02_Shadertoy/light-test.jpg" alt="Light test" />
  <img src="/src/assets/02_Shadertoy/animated-shader.gif" alt="Animated shader" />
  <img src="/src/assets/02_Shadertoy/shadow-test.jpg" alt="Shadow test" />
</div>

<style>
.grid-gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
  justify-items: center; /* centers each image in its grid cell */
}
</style>

<!-- caption -->
<figure class="center">
  <img src="/src/assets/02_Shadertoy/animated-shader.gif" alt="Animated shader" width="400" />
  <figcaption>Animated shader example created in my Shadertoy Clone project</figcaption>
</figure>

<style>
figure {
  margin: 1rem 0;
}
figcaption {
  font-size: 0.9rem;
  color: #666;
  text-align: center;
}
</style>