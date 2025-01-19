<template>
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
        <!-- <div class="mb-10"> dit is het 'terug' pijltje
            <NuxtLink to="/">
                <span>
                    <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24">
                        <path fill="currentColor" d="m6.921 12.5l5.793 5.792L12 19l-7-7l7-7l.714.708L6.92 11.5H19v1z">
                        </path>
                    </svg>
                </span>
                <span class="text-xs">Back</span>
            </NuxtLink>
        </div> -->
        <h1 class="text-4xl pt-12"> Contact </h1>
        <p> feel free to contact me if you have a question or if you want to work together ! </p>
        <p class="pt-6"> you can reach me at<br>
            +32123456789 <br>
            email.adres@gmail.com
        </p>
        <p class="pt-6"> or you can leave a message here </p>
        <el-input v-model="input" style="width: 240px" placeholder="message ..." />
    </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
const input = ref('')
</script>
<style>
.header {
    padding: 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
</style>
