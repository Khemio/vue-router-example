<template>
    <section v-if="experience">
        <h1>{{experience.name}}</h1>
        <img :src="`/images/${experience.image}`" :alt="experience.name">
        <p>{{experience.description}}</p>
    </section>
</template>

<script setup>
import { ref } from 'vue';
import sourceData from '../data.json'

const {id, experienceSlug} = defineProps({
    id: {type: Number, required: true},
    experienceSlug: {type: String, required: true}
})

const destination = ref(null);
const experience = ref(null);

const updateDestination = () => {
    destination.value = sourceData.destinations.find(destination => destination.id === id);
}

const updateExperience = () => {
    updateDestination();
    experience.value = destination.value.experiences.find(experience => experience.slug === experienceSlug);
}

updateExperience()

</script>