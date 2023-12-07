<script>
import AppCard from './AppCard.vue'
import { store } from '../store';

export default {
    name: 'AppMain',
    components: {
        AppCard,
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
        <!-- section movie -->
        <section>
            <h2 v-if="store.movies.length > 0 || store.movies == 0 && store.apiResponse" class="text-center text-light">Movies</h2>
            <div class="d-flex flex-wrap justify-content-center">
                <!-- AppMovie card -->
                <AppCard class="mb-3" v-for="movie in store.movies" :card="movie"/>
            </div>
        </section>

        <p v-if="(store.movies == 0 && store.apiResponse)" class="fs-4 notFound text-center">
            Whoops movie is not available
        </p>
        
        <!-- section tv series -->
        <section>
            <h2 v-if="store.series.length > 0 || store.movies == 0 && store.apiResponse" class="text-center text-light">Series</h2>
            <div class="d-flex flex-wrap justify-content-center">
                <!-- AppMovie card -->
                <AppCard class="mb-3" v-for="serie in store.series" :card="serie"/>
            </div>
        </section>

        <p v-if="(store.series == 0 && store.apiResponse)" class="fs-4 notFound text-center">
            Whoops serie is not available
        </p>
    </div>
</template>

<style scoped>
h2 {
    font-family: 'Silkscreen', sans-serif;
    font-size: 3rem;
}

.notFound {
    color: red;
}
</style>
