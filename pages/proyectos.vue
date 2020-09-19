<template lang="pug">
  main(class='flex flex-col pt-24 pb-8 w-3/4 border-b-2 border-gray-400')
    div.py-6.text-pink-800.font-bold.text-xl
      | Proyectos
    div.py-6.text-justify
      p Algunos de mis trabajos, espero te gusten !!!
    ul(class='grid gap-2 grid-cols-1 sm:grid-cols-2 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-3')
      li.flex.justify-center.py-2(v-for='p in proyects' :key='p.slug')
        NuxtLink(:to="`/projects/${p.slug}`")
          div.cardProject(:style="`--animation-order: ${p.index}`")
            h3.title {{ p.title }}
            div.bar
              div.emptybar
              div.filledbar
            div.circle
              svg(version="1.1" xmlns="http://www.w3.org/2000/svg")
                circle.stroke(cx="60" cy="60" r="50")
</template>

<script>
export default {
  name: 'Proyectos',
  async asyncData({ $content, params }) {
    const proyects = await $content('projects', params.slug)
      .only(['title', 'slug', 'createdAt', 'description', 'index', 'tags'])
      .sortBy('index', 'asc')
      .fetch()
    return { proyects }
  },
}
</script>

<style scoped>
:root {
  --base-grid: 8px;
  --colour-body-background: #97266d;
  --colour-background: #fff;
  --colour-background-folded: #f5f5f5;
  --colour-background-stripes: rgba(255, 255, 255, 0.5);
  --colour-text: #1a1a1a;
}

.cardProject {
  display: flex;
  height: 280px;
  width: 60vw;
  background-color: #17141d;
  border-radius: 10px;
  box-shadow: -0.5rem 0 1rem var(--colour-body-background);
  transition: 0.4s ease-out;
  position: relative;
  left: 0px;
}

.cardProject:not(:first-child) {
  margin-left: -50px;
}

.cardProject:hover {
  transform: translateY(-20px);
  transition: 0.4s ease-out;
}

.cardProject:hover ~ .cardProject {
  position: relative;
  left: 50px;
  transition: 0.4s ease-out;
}

.title {
  color: white;
  font-weight: 300;
  position: absolute;
  left: 20px;
  top: 15px;
}

.bar {
  position: absolute;
  top: 100px;
  left: 20px;
  height: 5px;
  width: 150px;
}

.emptybar {
  background-color: #2e3033;
  width: 100%;
  height: 100%;
}

.filledbar {
  position: absolute;
  top: 0px;
  z-index: 3;
  width: 0px;
  height: 100%;
  background: rgb(0, 154, 217);
  background: linear-gradient(
    90deg,
    rgb(255, 255, 255) 0%,
    rgb(19, 68, 181) 65%,
    rgb(149, 8, 141) 100%
  );
  transition: 0.6s ease-out;
}

.cardProject:hover .filledbar {
  width: 120px;
  transition: 0.4s ease-out;
}

.circle {
  position: absolute;
  top: 150px;
  left: calc(50% - 60px);
}

.stroke {
  stroke: white;
  stroke-dasharray: 360;
  stroke-dashoffset: 360;
  transition: 0.6s ease-out;
}

svg {
  fill: #17141d;
  stroke-width: 2px;
}

.cardProject:hover .stroke {
  stroke-dashoffset: 100;
  transition: 0.6s ease-out;
}
</style>
