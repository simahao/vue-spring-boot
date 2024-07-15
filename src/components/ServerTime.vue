<template>
    <div id="app">
        <button @click="fetchTime">Get Server Time</button>
        <p v-if="serverTime">Server Time: {{ serverTime }}</p>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name: 'app',
    data() {
        return {
            serverTime: null
        }
    },
    methods: {
        fetchTime() {
            axios.get('/api/curtime')
                .then(response => {
                    this.serverTime = response.data;
                })
                .catch(error => {
                    console.log(error);
                })
        }
    }
}
</script>