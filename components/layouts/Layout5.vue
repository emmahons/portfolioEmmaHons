<template>
  <div class="layout5">
    <ClientOnly>
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
      <div class="container">
        <h1 class="text-3xl text-center md:text-3xl lg:text-6xl lg:mb-10 font-bold">{{ data.title }}</h1>

        <div v-if="data.imagegallery && data.imagegallery.showgallery == true" class="pt-10 pb-20">
          <ImageGallery />
        </div>

        <div class="text-xs leading-3 container">
          <hr>
          <p class="text-xs opacity-50 hover:opacity-100 pb-5">Last update: {{ formatDate(data.date) }}</p>
          <article v-if="data.tags" class="tags">
            <li v-for="(item, index) in data.tags" :key="index" class="pt-2 text-xs opacity-50 hover:opacity-100">
              <NuxtLink :to="`/tags/${item}`">{{ item }}</NuxtLink>
            </li>
          </article>
        </div>
      </div>


      <!-- SEO metadata -->
      <!-- Regular Meta Tags -->
      <Title>{{ data.title }}</Title>
      <Meta name="description" :content="data.description" />
      <Meta name="tags" :content="data.tags" />
      <!-- Open Graph Meta Tags -->
      <Meta property="og:title" :content="data.title" />
      <Meta property="og:description" :content="data.description" />
      <Meta property="og:image" :content="data.thumbnail" /> <!-- Add an image URL here -->
      <Meta property="og:url" :content="data.url" /> <!-- Add the current URL -->
      <Meta property="og:type" content="article" />

    </ClientOnly>
  </div>
</template>

<script setup>
defineProps(['data', 'formatDate']);
</script>

<style>
.header {
    padding: 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
</style>