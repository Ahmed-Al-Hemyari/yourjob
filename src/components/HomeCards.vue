<script setup>
    import { RouterLink } from 'vue-router';
</script>
<template>
    <div class="flex flex-col md:flex-row justify-center mb-5">
        <!-- Card One -->
        <div :class="`my-4 mx-6 p-6 bg-gary-100 shadow-lg rounded-3xl flex flex-col items-center space-y-3`">
            <div class="space-y-3 w-full flex flex-col">
                <h1 class="font-bold text-2xl">For Job Seekers</h1>
                <p class="text-lg">Browse our jobs and start your career today</p>
            </div>
            <RouterLink to="/jobs" class="my-4 p-3 px-15 bg-black text-center text-white rounded-xl">Browse Jobs</RouterLink>
        </div>
        <!-- Card Two -->
        <div :class="`my-4 mx-6 p-6 bg-yellow-100 shadow-lg rounded-3xl flex flex-col items-center space-y-3`">
            <div class="space-y-3 w-full flex flex-col">
                <h1 class="font-bold text-2xl">For Employers</h1>
                <p class="text-lg">List your job to find the perfect empolyee for the role</p>
            </div>
            <RouterLink to="/jobs/add" class="my-4 p-3 px-15 bg-[var(--color-golden)] text-center text-white rounded-xl">Add Job</RouterLink>
        </div>
    </div>
</template>
