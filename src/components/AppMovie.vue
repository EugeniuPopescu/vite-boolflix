<script>

export default {
    name: 'AppMovie',
    props: {
        card: Object
    },
    mounted() {
        console.log('Creato AppMovie');
    }
}
</script>

<template>
    <!-- AppMovie, movie card -->
    <div class="box bg-dark text-light p-2 mx-2">
        <div class="text-center">
            <p class="fs-4"><span class="fw-bold text-warning">Titolo: </span> {{ card.title }}</p>
            <p><span class="fw-bold text-warning">Titolo Originale: </span> {{ card.original_title }}</p>
        </div>
        <p><span class="fw-bold text-warning">Voto: </span> {{ card.vote_average }}</p>
        <p><span class="fw-bold text-warning">Lingua Originale: </span> {{ card.original_language }}</p>
        <p><span class="fw-bold text-warning">Overview: </span> {{ card.overview }}</p>
    </div>
</template>

<style scoped>
.box {
    width: 18%;
    height: 20rem;
}
</style>
