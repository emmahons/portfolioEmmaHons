<template>
  <div>
    <div class="header "><!-- dit is het hamburgermenu-->
      <NuxtLink to="/">
        <svg xmlns="http://www.w3.org/2000/svg" width="2em" height="2em" viewBox="0 0 24 24">
          <path fill="currentColor"
            d="M5.692 19V9.946L2.604 12.25L2 11.458L12 4l4.346 3.223V5h1.885v3.639l3.788 2.819l-.603.792l-3.089-2.304V19h-5.096v-5.23h-2.462V19zm1-1H9.77v-5.23h4.462V18h3.096V9.21L12 5.256L6.692 9.21zm3.5-7.994h3.616q0-.704-.542-1.159q-.543-.455-1.266-.455t-1.265.453t-.543 1.16M9.77 18v-5.23h4.462V18v-5.23H9.769z">
          </path>
        </svg>
      </NuxtLink>
      <Drawer />
    </div>
    <main class="mx-auto max-w-6xl space-y-12 pt-12 ">
      <div class="text-3xl font-bold">
        Work
      </div>
      <!-- Responsive Masonry Layout -->
      <div class="masonry grid-cols-2">
        <div class="masonry-item px-2" v-for="post in posts" :key="post.slug">
          <div class="masonry-image  ">
            <NuxtImg :src="post.thumbnail" alt="Post thumbnail" class="w-full h-64 object-cover mb-2" :width="750"
              :height="550" />
          </div>
          <NuxtLink :to="post._path" class="block">
            <div class="masonry-item-text mb-12">
              <h2 class="text-xl font-semibold mb-2  ">{{ post.title }}</h2>
              <!-- Limiting the height of the description and making it responsive -->
              <p v-if="post.description" class="text-gray-600 line-clamp-3 ">{{ post.description }}</p>
              <ClientOnly>
                <article v-if="post.tags" class="text-xs mt-2 ">
                  <li v-for="(item, index) in post.tags" :key="index" class="inline mr-2 ">
                    <NuxtLink :to="`/tags/${item}`">{{ item }}</NuxtLink>
                  </li>
                </article>
              </ClientOnly>
            </div>
          </NuxtLink>



        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
const { data: posts } = await useAsyncData('posts', () => {
  return queryContent('/page')
    .sort({ promoted: 1 })

    .find()
})
</script>

<style>
.post .darkmode {
  color: white;
}
</style>