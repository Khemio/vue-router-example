<template>
    <div>
        <h1>Greetings, {{username}}</h1>
        <button @click="logout">Logout</button>
        <router-link :to="{name: 'invoices'}">
            <button>Invoices</button>
        </router-link>
    </div>

</template>
<script setup>
import { ref } from 'vue';
import {useRouter} from 'vue-router';

const router = useRouter();

const username = ref(window.user);

const logout = () => {
    window.user = null;
    router.push({name: 'Home'})
}
</script>