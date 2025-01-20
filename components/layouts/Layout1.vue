<template>
  <div class="layout1 ">
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
        <h1 class="text-3xl md:text-3xl lg:text-6xl lg:mb-10 font-bold">{{ data.title }}</h1>
        <NuxtImg v-if="data.thumbnail" :src="data.thumbnail" class="pb-6 w-screen bg-cover " />
        <div class="grid lg:grid-cols-2 gap-x-6 sm:grid-cols-1 ">
          <div>
            <p class=" pb-10 ">
              <ContentRenderer :value="data" />
            </p>
          </div>
          <div v-if="data.uitleg" class="">
            <p> {{ data.uitleg }}</p>
          </div>
        </div>

        <div v-if="data.imagegallery && data.imagegallery.showgallery == true" class="pt-10 pb-20">
          <ImageGallery />
        </div>

        <div class="text-xs leading-3 container">
          <hr class="">
          <p class="text-xs opacity-50 hover:opacity-100 pb-5">Last update: {{ formatDate(data.date) }}</p>
          <article v-if="data.tags" class="tags">
            <li v-for="(item, index) in data.tags" :key="index" class="pt-2 text-xs opacity-50 hover:opacity-100">
              <NuxtLink :to="`/tags/${item}`">{{ item }}</NuxtLink>
            </li>
            <el-backtop :right="200" :bottom="100" class="" /> <!-- back to top element -->
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
.el-backtop {
  color: rgb(56, 55, 55);
  background-color: transparent;
  box-shadow: none;
}

.header {
  padding: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>