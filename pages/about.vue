<template>
    <div>
        <div class="pr-5">
            <Drawer />
        </div>
        <div class="pl-5">
            <NuxtLink to="/">
                <svg xmlns="http://www.w3.org/2000/svg" width="2em" height="2em" viewBox="0 0 24 24">
                    <path fill="currentColor"
                        d="M5.692 19V9.946L2.604 12.25L2 11.458L12 4l4.346 3.223V5h1.885v3.639l3.788 2.819l-.603.792l-3.089-2.304V19h-5.096v-5.23h-2.462V19zm1-1H9.77v-5.23h4.462V18h3.096V9.21L12 5.256L6.692 9.21zm3.5-7.994h3.616q0-.704-.542-1.159q-.543-.455-1.266-.455t-1.265.453t-.543 1.16M9.77 18v-5.23h4.462V18v-5.23H9.769z">
                    </path>
                </svg>
            </NuxtLink>
        </div>
        <div class="container grid grid-cols-2 ">
            <h1 class="text-4xl pt-12">About me </h1>
            <div></div>

            <NuxtImg height=300 src="/img//mij2.jpeg" class="" />
            <p class="pt-3"> Hello! I’m Emma, a student in Media- & Information Design at Luca School of Arts in
                Brussels. I am
                very
                passionate about my work and always try to give my 100% when working on a project. I love design
                (obviously), but also love music, books, good food & coffee. <br>
                If you have a
                question, are interested in working together, or just want to talk: don’t hesitate!</p>
        </div>
    </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'

const activeName = ref('1')
</script>

<style>
.container {
    max-width: 70vw;
}
</style>