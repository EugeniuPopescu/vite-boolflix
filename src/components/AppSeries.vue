<script>

export default {
    name: 'AppSeries',
    props: {
        card: Object
    },
    mounted() {
        console.log('Creato AppSeries');
    }
}
</script>

<template>
    <!-- AppContent, signle mouvie card -->
    <div class="box bg-dark text-light p-2">
        <p class="fs-4"><span class="fw-bold">Titolo: </span> {{ card.title }}</p>
        <p><span class="fw-bold">Voto: </span> {{ card.vote_average }}</p>
        <p><span class="fw-bold">Titolo Originale: </span> {{ card.original_title }}</p>
        <p><span class="fw-bold">Lingua Originale: </span> {{ card.original_language }}</p>
        <p><span class="fw-bold">Overview: </span> {{ card.overview }}</p>
    </div>
</template>

<style scoped>
.box {
    width: 30%;
    height: 35rem;
}
</style>