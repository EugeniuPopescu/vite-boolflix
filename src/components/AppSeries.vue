<script>

export default {
    name: 'AppSeries',
    props: {
        card: Object
    },
    mounted() {
        console.log('Creato AppSeries');
    },
    methods: {
        getFlags(flag) {
            return new URL(`/public/flags/${flag}.svg`, import.meta.url).href;
        }
    }
}
</script>

<template>
    <!-- AppSeries, serie card -->
    <div class="box bg-dark text-light p-2 mx-2">
        <div class="text-center">
            <!-- title -->
            <p class="fs-4"><span class="fw-bold text-warning">Titolo: </span> {{ card.title }}</p>
            <!-- original title -->
            <p><span class="fw-bold text-warning">Titolo Originale: </span> {{ card.original_title }}</p>
        </div>
        <!-- vote -->
        <p><span class="fw-bold text-warning">Voto: </span> {{ card.vote_average }}</p>
        <!-- original language -->
        <p><span class="fw-bold text-warning">Lingua Originale: </span > {{ card.original_language }}</p>
        <!-- flag -->
        <div class="d-flex justify-content-center">
            <img :src="getFlags(card.original_language)" alt="flag">
        </div>
        <!-- overview -->
        <p><span class="fw-bold text-warning">Overview: </span> {{ card.overview }}</p>
    </div>
</template>

<style scoped>
img {
    width: 3rem;
    height: 2rem;
}
.box {
    width: 18%;
    height: 20rem;
}
</style>