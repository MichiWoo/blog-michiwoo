<template lang="pug">
  main(class='w-4/5 flex flex-col justify-between content-center pt-8 pb-8 w-4/5 border-b-2 border-gray-400')
    div(class="flex justify-center items-center sm:justify-start sm:py-4 py-6")
      div.flex-initial
        Rocket
      div(class="sm:flex-grow flex-col justify-center items-center sm:justify-start ml-4")
        h1(class='text-pink-primary font-bold sm:text-3xl text-2xl') Michel González
        span.font-medium.text-gray-800 Frontend developer & coffee fan &#x2615
    ul(class='grid gap-2 grid-cols-1 sm:grid-cols-2 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-3')
      li(v-for='b in blog' :key='b.slug')
        NuxtLink(:to="`/blog/${b.slug}`")
          div.card.mx-2(:style="`--animation-order: ${b.index}`")
            div.articles__article
              a.articles__link
                div.articles__content.articles__content--lhs
                  h2.articles__title {{ b.title }}
                  div(v-html='getTags(b)')
                  div.articles__footer
                    time {{ formatDate(b.updatedAt) }}
                div.articles__content.articles__content--rhs(aria-hidden="true")
                  h2.articles__title {{ b.title }}
                  div(v-html='getTags(b)')
                  div.articles__footer
                    time {{ formatDate(b.updatedAt) }}
</template>

<script>
export default {
  name: 'Home',
  components: {
    Rocket: () => import('../components/Rocket'),
  },
  props: {
    blog: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    getTags(blog) {
      let html = ''
      const tags = blog.tags.split(' ')
      tags.map((t) => {
        html += `<span class='inline-block bg-pink-primary rounded-full px-2 py-1 text-sm font-base text-white mr-1 mb-1'>${t}</span>`
      })
      return html
    },
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('es', options)
    },
  },
}
</script>

<style>
:root {
  --base-grid: 8px;
  --colour-body-background: #95088d;
  --colour-background: #fff;
  --colour-background-folded: #f5f5f5;
  --colour-background-stripes: rgba(255, 255, 255, 0.5);
  --colour-text: #1a1a1a;
}
.articles {
  margin: calc(var(--base-grid) * 2) auto calc(var(--base-grid) * 5);
  display: grid;
  grid-row-gap: calc(var(--base-grid) * 8);
  grid-column-gap: calc(var(--base-grid) * 6);
  grid-template-columns: repeat(
    auto-fit,
    minmax(calc(var(--base-grid) * 35), 1fr)
  );
  justify-items: center;
}

.articles__article {
  cursor: pointer;
  display: block;
  position: relative;
  perspective: 1000px;
  animation-name: animateIn;
  animation-duration: 0.35s;
  animation-delay: calc(var(--animation-order) * 100ms);
  animation-fill-mode: both;
  animation-timing-function: ease-in-out;
}

.articles__article:before {
  content: '';
  position: absolute;
  top: calc(var(--base-grid) * -2);
  left: calc(var(--base-grid) * -2);
  border: 2px dashed var(--colour-background);
  background-image: repeating-linear-gradient(
    -24deg,
    transparent,
    transparent 4px,
    var(rgba(255, 255, 255, 0.5) 0, var(rgba(255, 255, 255, 0.5) 5px))
  );
  z-index: -1;
}

.articles__article,
.articles__article:before {
  width: calc(var(--base-grid) * 35);
  height: calc(var(--base-grid) * 35);
}

.articles__link {
  background-color: var(--colour-body-background);
  border: 2px solid var(--colour-background);
  display: block;
  width: 100%;
  height: 100%;
}

.articles__link:after {
  content: '';
  position: absolute;
  top: 50%;
  right: calc(var(--base-grid) * 3);
  width: calc(var(--base-grid) * 2);
  height: calc(var(--base-grid) * 2);
  margin-top: calc(var(--base-grid) * -1);
  clip-path: polygon(75% 0, 100% 50%, 75% 100%, 0 100%, 25% 50%, 0 0);
  -webkit-clip-path: polygon(75% 0, 100% 50%, 75% 100%, 0 100%, 25% 50%, 0 0);
  background-color: var(--colour-background);
  opacity: 0;
  transition: opacity 0.5s ease-in, transform 0.3s ease-in-out 0ms;
}

.articles__content {
  background-color: var(--colour-background);
  color: var(--colour-text);
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  padding: calc(var(--base-grid) * 2);
  display: flex;
  flex-direction: column;
  border: 2px solid rgba(151, 38, 109, 0.08);
}

.articles__content--lhs {
  clip-path: polygon(0 0, 51% 0, 51% 100%, 0 100%);
  -webkit-clip-path: polygon(0 0, 51% 0, 51% 100%, 0 100%);
}

.articles__content--rhs {
  clip-path: polygon(50% 0, 100% 0, 100% 100%, 50% 100%);
  -webkit-clip-path: polygon(50% 0, 100% 0, 100% 100%, 50% 100%);
  transition: transform 0.5s ease-in-out, background-color 0.4s ease-in-out;
}

.articles__title {
  font-size: calc(var(--base-grid) * 4);
  line-height: 1.125;
  font-weight: 700;
  letter-spacing: -0.02em;
  margin-bottom: 0.2em;
}

.articles__footer {
  margin-top: auto;
  font-size: calc(var(--base-grid) * 2);
  line-height: calc(var(--base-grid) * 2);
  display: flex;
  justify-content: space-between;
}

.articles__link:hover .articles__content--rhs {
  background-color: var(--colour-background-folded);
  transform: rotateY(-50deg);
}

.articles__link:hover:after {
  opacity: 1;
  transform: translateX(calc(var(--base-grid) * 1.5));
  transition: opacity 0.5s ease-in, transform 0.3s ease-in-out 0.25s;
}

@media only screen and (max-width: 768px) {
  .articles__article,
  .articles__article:before {
    width: 80vw;
    height: calc(var(--base-grid) * 25);
  }
  .articles__title {
    font-size: 22px;
    margin-bottom: 0.4em;
  }
  .articles__footer {
    font-size: 16px;
    line-height: calc(var(--base-grid) * 1);
  }
}
</style>
