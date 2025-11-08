<script setup>
    import { onMounted, reactive, defineProps } from 'vue';
    import { RouterLink } from 'vue-router';
    import axios from 'axios';
    import JobListing from './JobListing.vue';
    import jobs from '../jobs.json';

    defineProps({
        limit: Number,
        showAllButton: Boolean,
    })

    const state = reactive({
        jobs: [],
        isLoading: true
    });

    onMounted(() => {
        try {
            const response = jobs;
            state.jobs = response.jobs;
        } catch (error) {
            console.error("Error fetching Data", error);
        }
        finally {
            state.isLoading = false;
        }
    })
</script>

<template>
    <div class="bg-yellow-100 p-5">
        <h1 class="p-5 text-[var(--color-golden)] text-center  text-3xl font-extrabold" >Browse Jobs</h1>
        <div v-if="state.isLoading" class="flex flex-col">
            <i class="pi pi-spin pi-spinner text-5xl mx-auto"></i>
        </div>
        <div v-else class="grid grid-cols-1 md:grid-cols-3 gap-6">
            <JobListing v-for="job in state.jobs.slice(0, limit || state.jobs.length)" :job="job" :key="job.id"/>
        </div>
        <section v-if="showAllButton" class="flex items-center justify-center p-6">
            <RouterLink to="/jobs" class="w-1/2 p-3 px-15 bg-black text-center text-white rounded-xl">View All Jobs</RouterLink>
        </section>
    </div>
</template>