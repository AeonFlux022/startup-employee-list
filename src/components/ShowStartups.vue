<template>
    <div class="container" id="showStartups">
        <table class="table table-striped table-hover">
            <thead>
                <tr>
                <th>
                    ID
                </th>
                <th>
                    Startup Name
                </th>
                <th>
                    Category
                </th>
                <th>
                    Owner
                </th>
                <th>
                    Description
                </th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(startup, index) in startups" :key="startup.id">
                    <td>{{index + 1}}</td>
                    <td>{{startup.name}}</td>
                    <td>{{startup.category}}</td>
                    <td>{{startup.owner}}</td>
                    <td>{{startup.description}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
    
    
<script>
import axios from 'axios'

const baseURL = "http://localhost:3000/startups";

export default {
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