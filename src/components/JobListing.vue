<script setup>
    import { computed, defineProps, ref } from 'vue';
    import { RouterLink, useRoute } from 'vue-router';

    const props = defineProps({
        job: Object
    })

    const showFullDescription = ref(false);
    
    const toggleFullDescription = () => {
        showFullDescription.value = !showFullDescription.value;
    }

    const truncatedDescripton = computed(() => {
        let description = props.job.description;
        if (!showFullDescription.value){
            description = description.substring(0, 90) + "...";
        }
        return description;
    })
</script>

<template>
    <div class="m-2 p-6 bg-white shadow-lg rounded-3xl flex flex-col justify-between items-center space-y-3 ">
        <div class="space-y-3 w-full flex flex-col pb-5 border-b-1 border-b-gray-400">
            <p class="text-gray-500 text-xl">{{ job.type }}</p>
            <h1 class="font-bold text-xl">{{ job.title }}</h1>
            <div class="text-md">
                {{ truncatedDescripton }}
                <button class="text-[var(--color-golden)]" @click="toggleFullDescription">{{ showFullDescription ? "Less" : "More" }}</button>
            </div>
            <p class="text-sm text-[var(--color-golden)]">{{ job.salary }} / Year</p>
        </div>

        <div class="w-full my-1 p-1 space-x-2 flex flex-row justify-between items-center">
            <div class="text-orange-700 items-center">
                <li class="pi pi-map-marker mr-1"></li>
                {{ job.location }}
            </div>
            <RouterLink :to="`/jobs/${job.id}`" class="p-3 bg-[var(--color-golden)] text-center text-white rounded-xl">Read More</RouterLink>
        </div>
    </div>
</template>