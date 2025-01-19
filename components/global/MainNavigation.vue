<template>
  <div class="">

    <el-collapse accordion class="accordeon">
      <el-collapse-item title="Work" name="1" class="nuxtlink">
        <ul v-for="post in folders" :key="post.slug">
          <NuxtLink :to="post._path" :active-class='"active"'>
            <li class="leading-7 nuxtlink">{{ post.title }}</li>
          </NuxtLink>
        </ul>
        <NuxtLink to="/overview" class=" nuxtlink accordion italic">
          see all work
        </NuxtLink>
      </el-collapse-item>
    </el-collapse>

    <div class="links-container nuxtlink ">
      <NuxtLink to="/about" :active-class='"active"'>
        About
      </NuxtLink>
    </div>
    <div class="links-container nuxtlink ">
      <NuxtLink to="/contact" :active-class='"active"'>
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
  gap: 0;
  /* Optional: adds spacing between links */
  line-height: 40pt;
}

.links-container a {
  text-decoration: none;
  /* Optional: removes underline from the links */
}

.light-mode a:hover {
  color: #fcfcfc;
  font-family: "libre baskerville";
}

.gray-mode a:hover {
  color: #251603ef;
  font-family: "libre baskerville";
}

.dark-mode a:hover {
  color: #20211e;
  font-family: "libre baskerville";
}

:deep(.nuxtlink button:hover) {
  color: white !important;
  font-family: "libre baskerville";
}

.light-mode .active {
  color: #fcfcfc !important;
  font-family: "libre baskerville";
}

.gray-mode .active {
  color: #251603ef !important;
  font-family: "libre baskerville";
}

.dark-mode .active {
  color: #20211e !important;
  font-family: "libre baskerville";
}



.accordeon {
  --el-collapse-content-bg-color: none;
  --el-collapse-header-bg-color: none;
  --el-collapse-border-color: none;
  font-family: 'josefin sans';
  --el-collapse-border-color: none;
  --el-collapse-content-bg-color: none;
  --el-collapse-header-bg-color: none;
  --el-collapse-header-font-size: xx-large;
  --el-collapse-header-text-color: inherit;
  --el-collapse-content-text-color: inherit;
  --el-collapse-content-font-size: large;
}
</style>
