<template>
  <div class="">

    <el-collapse accordion class="">
      <el-collapse-item title="Work" name="1">
        <ul v-for="post in folders" :key="post.slug">
          <NuxtLink :to="post._path">
            <li class="leading-7">{{ post.title }}</li>
          </NuxtLink>
        </ul>
        <NuxtLink to="Page" class="accordion italic">
          see all work
        </NuxtLink>
      </el-collapse-item>
    </el-collapse>

    <div class="links-container">
      <NuxtLink to="about">
        About
      </NuxtLink>
      <NuxtLink to="contact">
        Contact
      </NuxtLink>
    </div>

  </div>
</template>

<script lang="ts" setup>
import { ref, onMounted } from 'vue';
import { useAsyncData } from '#app';

const activeNames = ref(['1']);
const handleChange = (val: string[]) => {
  console.log(val);
};

// Define a ref for storing folders
const folders = ref([]);

// Fetch all posts from both /folders and /page
const { data: foldersPosts } = await useAsyncData('folders', () => queryContent('/')
  .sort({ numbernavigation: 1 })
  .find());

// Combine and filter the data
onMounted(() => {
  const allPosts = [...(foldersPosts.value || [])];
  if (allPosts.length) {
    folders.value = allPosts.filter(post => post.included && post.included === true && post.included !== false);
  }
});
</script>

<style scoped>
.links-container {
  display: flex;
  flex-direction: column;
  /* Stack NuxtLink elements vertically */
  gap: 1rem;
  /* Optional: adds spacing between links */
}

.links-container a {
  text-decoration: none;
  /* Optional: removes underline from the links */
}
</style>
