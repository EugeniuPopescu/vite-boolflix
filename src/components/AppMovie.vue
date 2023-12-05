<script>
import { store } from '../store.js';
// import VueFlip from 'vue-flip';

export default {
    name: 'AppMovie',
    components: {
        // 'vue-flip': VueFlip
    },
    props: {
        card: Object
    },
    data() {
        return {
            store
        }
    },
    mounted() {
        console.log('Creato AppMovie');
    },
    methods: {
        getFlags(flag) {
            return new URL(`/public/flags/${flag}.svg`, import.meta.url).href;
        }
    }
}
</script>

<template>
    <!-- AppMovie, movie card -->
    <div class="box bg-dark text-light p-2 mx-2">

        <vue-flip>
            <div slot="front">
                <img v-if="card.poster_path" :src="store.coverImg + card.poster_path" alt="">
                <p v-else>img Not Aviable</p>
            </div>
            <div slot="back">
                <div class="text-center">
                    <!-- title -->
                    <p class="fs-4"><span class="fw-bold text-warning">Titolo: </span> {{ card.title }}</p>
                    <!-- original title -->
                    <p><span class="fw-bold text-warning">Titolo Originale: </span> {{ card.original_title }}</p>
                </div>
                <!-- vote -->
                <p><span class="fw-bold text-warning">Voto: </span> {{ card.vote_average }}</p>
                <!-- flag -->
                <div class="d-flex justify-content-center">
                    <img class="flag" v-if="this.store.flags.includes(card.original_language)"
                        :src="getFlags(card.original_language)" alt="flag">
                </div>
                <!-- originl language -->
                <p><span class="fw-bold text-warning">Lingua Originale: </span> {{ card.original_language }}</p>
                <!-- overview -->
                <p><span class="fw-bold text-warning">Overview: </span> {{ card.overview }}</p>
            </div>
        </vue-flip>

        
    </div>
</template>

<style scoped>
.flag {
    width: 3rem;
    height: 2rem;
}

.box {
    width: 18%;
    height: 20rem;
}

img {
    width: 100%;
    height: 100%;
}
</style>
