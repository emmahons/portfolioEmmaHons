<template>
  <div class="layout2 mt-6">
    <ClientOnly>
      <div class="relative max-h-screen overflow-hidden z-1">
        <!-- Lazy loading applied to NuxtImg 
      <NuxtImg
        v-if="data.thumbnail"
        :src="data.thumbnail"
        class="w-screen opacity-80 bg-cover"
        :alt="`Thumbnail for ${data.title}`"
        format="webp"
        loading="lazy"
        @load="imageLoaded = true"
      /> -->

        <div v-if="!imageLoaded" class="absolute inset-0 flex items-center justify-center bg-black bg-opacity-75">
          <div class="spinner"></div>
        </div>

        <div
          class="absolute inset-0 flex flex-col items-center justify-center bg-black bg-opacity-50 animate-fade animate-once animate-delay-[500ms]"
          v-if="imageLoaded">
          <div class="container p-4">
            <div>
              <h1 class="text-white text-4xl md:text-6xl lg:text-8xl font-bold">{{ data.title }}</h1>
              <h1 v-if="data.subtitle"
                class="text-white opacity-80 pt-3 text-xl md:text-2xl lg:text-3xl font-bold pb-10">{{ data.subtitle }}
              </h1>
            </div>

            <div>
              <p v-if="data.author" class="text-white opacity-80 text-xs font-bold">{{ data.author }}</p>
              <p class="text-white text-xs opacity-50 hover:opacity-100">Last update: {{ formatDate(data.date) }}</p>
            </div>
          </div>
        </div>
      </div>

      <!-- Loading Drawer component -->
      <div class="absolute top-0 right-0 z-10 pr-5">
        <Drawer />
      </div>

      <!-- Main section -->
      <div class="container mx-auto p-4 animate-fade animate-once animate-delay-[500ms]">
        <div class="grid grid-cols-3 md:grid-cols-3 gap-4 mt-6">
          <!-- First column -->
          <div>
            <h1 class="text-3xl md:text-3xl lg:text-6xl lg:mb-3 font-bold col-3">{{ data.title }}</h1>
            <h1 v-if="data.subtitle" class="opacity-80 text-xl md:text-2xl lg:text-3xl font-bold pb-10">{{
              data.subtitle }}</h1>
            <p class="text-lg md:text-2xl lg:text-xl pb-5 font-bold">{{ data.description }}</p>
          </div>
          <div></div>
          <div class="col-start-1 col-end-3">
            <ContentRenderer :value="data" />
          </div>


          <div v-if="data.imagegallery && data.imagegallery.showgallery == true" class=" col-start-2 col-end-4 mt-12">
            <ImageGallery />
          </div>
          <div></div>
          <div v-if="data.uitleg" class="col-start-1 col-end-3">
            <p> {{ data.uitleg }}</p>
          </div>
          <NuxtImg v-if="data.imagezgallery" :src="data.imagezgallery == true" class="col-start-2 col-end-4 mt-12"/>
        </div>

        <!-- Second row -->
        <div v-if="data.related_page">
          <RelatedPages :relatedPages="data.related_page" />
        </div>

        <!-- Link and published date -->
        <div class="text-xs leading-3">
          <hr />
          <p class="text-xs opacity-50 hover:opacity-100 pb-2">Last update: {{ formatDate(data.date) }}</p>
          <article v-if="data.tags" class="tags">
            <li v-for="(item, index) in data.tags" :key="index" class="pt-2 text-xs opacity-50 hover:opacity-100">
              <NuxtLink :to="`/tags/${item}`">{{ item }}</NuxtLink> <!-- Load NuxtLink -->
            </li>
          </article>
          <el-backtop :right="200" :bottom="100" class="" /> <!-- back to top element -->
        </div>
      </div>

      <!-- SEO metadata -->
      <Title>{{ data.title }}</Title>
      <Meta name="description" :content="data.description" />
      <Meta property="og:title" :content="data.title" />
      <Meta property="og:description" :content="data.description" />
      <Meta property="og:image" :content="data.thumbnail" />
      <Meta property="og:url" :content="data.url" />
      <Meta property="og:type" content="article" />
    </ClientOnly>
  </div>

</template>

<script setup>
import { ref } from 'vue';
const imageLoaded = ref(false);

defineProps(['data', 'formatDate']);
</script>

<style scoped>
.spinner {
  border: 4px solid rgba(255, 255, 255, 0.3);
  border-top: 4px solid #fff;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}
</style>
