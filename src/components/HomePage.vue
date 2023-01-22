<template>
<div class="container" id="home">
    <main>
    <div class="row" v-for="startup in startups" :key="startup.id">
        <div class="col justify-content-start">
            <div class="card text-white bg-primary mb-3">
            <div class="card-header">
                <h1> {{ startup.name }}</h1>
            </div>
            <div class="card-body">
            <h4 class="card-title">{{ startup.owner }}</h4>
            <p class="card-text">{{ startup.description }}</p>
            </div>
            </div>
        </div>
    </div>
    </main>
</div>
</template>

<script>
import axios from 'axios'
    
const baseURL = "http://localhost:3000/startups";

export default {
    name: 'HomePage',
    data() {
        return {
            startups: [],
        }
    },
    async created() {
        try {
            const res = await axios.get(baseURL);
            this.startups = res.data;
        } catch (e) {
            console.error(e);
        }
    }
}

</script>

<style>

</style>