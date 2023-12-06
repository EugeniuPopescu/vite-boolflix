<script>
import AppMovie from './AppMovie.vue'
import AppSeries from './AppSeries.vue'
import { store } from '../store';

export default {
    name: 'AppMain',
    components: {
        AppMovie,
        AppSeries
    },
    data() {
        return {
            store
        }
    },
    methods: {
        
    },
    mounted() {
        console.log('Creato AppMain');
    }
}
</script>

<template>
    <div class="container">
        <h2 v-if="store.movies.length > 0" class="text-center text-light">Movies</h2>
        <div class="d-flex flex-wrap justify-content-center">
            <!-- AppMovie card -->
            <AppMovie class="mb-3" v-for="movie in store.movies" :card="movie"/>
        </div>
        <!-- AppSeries card -->
        <h2 v-if="store.series.length > 0" class="text-center text-light">Series</h2>
        <div class="d-flex flex-wrap justify-content-center">
            <!-- AppMovie card -->
            <AppSeries class="mb-3" v-for="serie in store.series" :card="serie"/>
        </div>
    </div>
</template>

<style scoped>
h2 {
    font-family: 'Silkscreen', sans-serif;
    font-size: 3rem;
}
</style>
