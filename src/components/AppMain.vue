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
        <h2 v-if="store.movies.length > 0" class="text-center text-warning">Movies</h2>
        <div class="d-flex flex-wrap justify-content-around">
            <!-- AppMovie card -->
            <AppMovie class="mb-3" v-for="movie in store.movies" :card="movie"/>
        </div>
        <!-- AppSeries card -->
        <h2 v-if="store.series.length > 0" class="text-center text-warning">Series</h2>
        <div class="d-flex flex-wrap justify-content-around">
            <!-- AppMovie card -->
            <AppSeries class="box mb-3" v-for="serie in store.series" :card="serie"/>
        </div>
    </div>
</template>

<style scoped>
</style>
