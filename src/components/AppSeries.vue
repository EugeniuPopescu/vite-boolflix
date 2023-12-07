<script>
import { store } from '../store.js';

export default {
    name: 'AppSeries',
    props: {
        card: Object
    },
    data() {
        return {
            store
        }
    },
    mounted() {
        console.log('Creato AppSeries');
    },
    methods: {
        getFlags(flag) {
            return new URL(`/public/flags/${flag}.svg`, import.meta.url).href;
        },
        getVote(n) {
            return Math.round(n/2);
        }
    }
}
</script>

<template>
    <!-- AppSeries, serie card -->
    <div class="box text-light p-2 mx-2">




        <!-- flip card -->
        <div class="flip-card">
            <div class="flip-card-inner">
                <!-- front -->
                <div class="flip-card-front d-flex justify-content-center align-items-center">
                    <img v-if="card.poster_path" :src="store.coverImg + card.poster_path" alt="">
                    <p v-else class="fs-4">img Not Aviable 🥲</p>
                </div>

                <!-- back -->
                <div class="flip-card-back overflow-y-scroll">
                    <div class="back p-2">
                        <div class="text-center">
                            <!-- title -->
                            <p class="fs-4"><span class="fw-bold text-warning">Titolo: </span> {{ card.name }}</p>
                            <!-- original title -->
                            <p><span class="fw-bold text-warning">Titolo Originale: </span> {{ card.original_name }}</p>
                        </div>
                        
                        <!-- vote -->
                        <p><span class="fw-bold text-warning">Voto: </span>
                            <font-awesome-icon v-for="n in getVote(card.vote_average)" icon="fa-solid fa-star"
                            class="text-warning" />
                        </p>
                        
                        <!-- flag -->
                        <div class="d-flex justify-content-center">
                            <img class="flag" v-if="this.store.flags.includes(card.original_language)"
                            :src="getFlags(card.original_language)" alt="flag">
                        </div>
                        
                        <!-- original language -->
                        <p><span class="fw-bold text-warning">Lingua Originale: </span> {{ card.original_language }}</p>
                        
                        <!-- overview -->
                        <p><span class="fw-bold text-warning">Overview: </span> {{ card.overview }}</p>
                    </div>
                </div>
            </div>
        </div>
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

.back {
    background-color: black;
}
/* css flip */
.flip-card {
    background-color: transparent;
    width: 100%;
    height: 100%;
    perspective: 150rem;
}

/* This container is needed to position the front and back side */
.flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    transition: transform 0.8s;
    transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
}

/* Position the front and back side */
.flip-card-front,
.flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    /* Safari */
    backface-visibility: hidden;
}

/* Style the front side (fallback if image is missing) */
.flip-card-front {
    background-color: black;
    overflow: hidden;
}

/* Style the back side */
.flip-card-back {
    transform: rotateY(180deg);
    background-color: black;
}
</style>