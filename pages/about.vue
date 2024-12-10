<template>
    <div>
        <div class="pr-5">
            <Drawer />
        </div>
        <div class="container grid grid-cols-2 ">
            <h1 class="text-4xl pt-12">About me </h1>
            <div></div>

            <NuxtImg height=300 src="/img//mij2.jpeg" class="rotate-90 pt-32 pl-8" />
            <p class="pt-3"> Hello! I’m Emma, a student in Media- & Information Design at Luca School of Arts in
                Brussels. I am
                very
                passionate about my work and always try to give my 100% when working on a project. If you have a
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