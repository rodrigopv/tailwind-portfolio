<template>
  <div class="flex min-h-full flex-col md:flex-row">
    <div class="flex flex-shrink-0 pt-20 md:min-h-full md:h-full w-full md:w-2/5 lg:w-1/5 bg-white flex-col px-3 place-content-around content-center">
      <div class="block">
        <h2 class="md:text-center text-xl font-semibold">
          <span class="font-normal text-gray-500">#{{ article.flexNumber }}:</span> {{ article.title }}
        </h2>
      </div>
      <div class="block">
        <p>{{ article.description }}</p>
      </div>
    </div>
    <div :class="article.backgroundColor ? article.backgroundColor : 'bg-green-300'" class="relative flex h-full overflow-auto flex-grow content-center justify-center items-center">
      <nuxt-content :document="article" />
      <NuxtLink
        v-if="prev"
        v-shortkey.once="['arrowleft']"
        :to="{ name: 'sketches-slug', params: { slug: prev.slug } }"
        class="absolute group block w-14 h-14 border hover:bg-white duration-300 z-10 left-4 rounded-full"
        @shortkey.native="navigate(prev.slug)"
      >
        <div class="flex content-center flex-row justify-center h-full">
          <span class="text-2xl leading-[3rem]">👈</span>
        </div>
        <span class="hidden group-hover:block text-xs text-center text-white">Previous</span>
      </NuxtLink>
      <NuxtLink
        v-if="next"
        v-shortkey.once="['arrowright']"
        :to="{ name: 'sketches-slug', params: { slug: next.slug } }"
        class="absolute group block w-14 h-14 border hover:bg-white duration-300 z-10 right-4 rounded-full"
        @shortkey.native="navigate(next.slug)"
      >
        <div class="flex content-center flex-row justify-center h-full">
          <span class="text-2xl leading-[3rem]">👉</span>
        </div>
        <span class="hidden group-hover:block text-xs text-center text-white">Next</span>
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  transition: 'page',
  async asyncData ({ $content, params }) {
    // fetch our article here
    const article = await $content('sketches', params.slug).fetch()

    const [prev, next] = await $content('sketches')
      .only(['title', 'slug'])
      .sortBy('createdAt', 'asc')
      .surround(params.slug)
      .fetch()

    return { article, prev, next }
  },
  methods: {
    navigate (to) {
      this.$router.push(to)
    }
  }
}
</script>

<style>
  .nuxt-content-container {
    display: flex;
    align-items: center;
  }
</style>
