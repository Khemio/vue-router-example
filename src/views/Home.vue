<template>
    <div class="home">
        <h1>All Destinations</h1>
        <button @click="addDynamicRoute">Add Dynamic Route</button>
        <router-link to="/dynamic">Visit Dynamic Route</router-link>
        <div class="destinations">
            <router-link v-for="destination in destinations" 
            :key="destination.id"
            :to="{name: 'destination.show', params: {id: destination.id, slug: destination.slug}}"
            >
    
                <h2>{{destination.name}}</h2>
                <img :src="`/images/${destination.image}`" :alt="destination.name">
            
            </router-link>
        </div>
    </div>
</template>

<script setup>
import { useRouter, isNavigationFailure, NavigationFailureType } from 'vue-router';
import sourceData from '../data.json'

const destinations = sourceData.destinations;
const router = useRouter();

const addDynamicRoute = async () => {
    const removeDynamicRoute = router.addRoute({
        path: '/dynamic',
        name: 'dynamic',
        component: () => import('../views/Login.vue'),

    })

    removeDynamicRoute();
}

</script>