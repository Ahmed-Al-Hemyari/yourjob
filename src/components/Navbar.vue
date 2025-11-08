<script setup>
    import { RouterLink, useRoute } from "vue-router";

    import logo from "../assets/YourJob.png"

    const isActive = (routePath) => {
      const route = useRoute();
      return routePath === route.path;
    }
</script>
<template>
    <div class="bg-[var(--color-darkGray)] border-b-2 border-b-[var(--color-golden)] flex flex-row p-6 space-x-6 justify-between h-25 items-center">
      <RouterLink to="/" class="image flex flex-row items-center">
        <img class="rounded-full w-10 h-10 mr-4" :src="logo" alt=""></img>
        <h1 class="text-white text-2xl font-medium hidden md:block">Your Job</h1>
      </RouterLink>
      <nav class="flex flex-row items-center space-x-10">
        <RouterLink to="/" :class="[isActive('/')?'text-[var(--color-golden)]':'text-white', 'font-medium', 'text-lg', 'hover:text-[var(--color-darkGolden)]']">Home</RouterLink>
        <RouterLink to="/jobs" :class="[isActive('/jobs')?'text-[var(--color-golden)]':'text-white', 'font-medium', 'text-lg', 'hover:text-[var(--color-darkGolden)]']">Jobs</RouterLink>
        <RouterLink to="/jobs/add" :class="['bg-[var(--color-golden)]','text-[var(--color-darkGray)]', 'px-3', 'py-1.5', 'rounded-full' , 'font-medium', 'text-lg', 'hover:bg-[var(--color-darkGolden)]']">Add Job</RouterLink>
      </nav>
    </div>
</template>