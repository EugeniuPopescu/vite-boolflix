<script>
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
import axios from 'axios';
import { store } from './store';


export default {
    components: {
        AppHeader,
        AppMain,
    },
    data() {
        return {
            store
        }
    },
    mounted() {
        console.log('API Key: 07817ee9ac4818e99a782b133fd5bf38');
    },
    methods: {
        getContents() {
            // movies
            const option = {
                method: 'GET',
                params: {
                    query: `${store.searchTitle}`,
                    include_adult: 'false',
                    language: 'it-IT',
                    page: '1',
                    api_key: '07817ee9ac4818e99a782b133fd5bf38'
                },

            };

            // movie
            option.url = 'https://api.themoviedb.org/3/search/movie';

            axios
            .request(option)
            .then(function (response) {
                console.log(response.data.results);
                store.movies = response.data.results;
                
                store.apiResponse = true;
            })
            .catch(function (error) {
                console.error(error);
                store.apiResponse = true;
            });

            // tv
            option.url = 'https://api.themoviedb.org/3/search/tv';

            axios
            .request(option)
            .then(function (response) {
                console.log(response.data.results);
                store.series = response.data.results;

                store.apiResponse = true;
            })
            .catch(function (error) {
                console.error(error);
                store.apiResponse = true;
            });
        }
    }
}
</script>

<template>
    <header class="d-flex align-items-center z-10">
        <AppHeader @search="getContents()" />
    </header>

    <main>
        <AppMain />
    </main>
</template>

<!-- scss -->
<style lang="scss">
@use './styles/general.scss';
</style>

<style scoped lang="scss">
header {
    height: 6rem;
    color: #CD1818;
    background-color: black;
}

main {
    height: calc(100% - 6rem);
}
</style>
