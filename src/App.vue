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
            const moviesUrl = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/search/movie',
                params: { query: `${store.searchTitle}`, 
                include_adult: 'false', 
                language: 'it-IT', 
                page: '1',
                api_key: '07817ee9ac4818e99a782b133fd5bf38' 
            },
                headers: {
                    accept: 'application/json',
                    // Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIwNzgxN2VlOWFjNDgxOGU5OWE3ODJiMTMzZmQ1YmYzOCIsInN1YiI6IjY1NmRiZmU5NGE0YmY2MDBjNTAzNTIwOCIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.RQk5iEa9mbLnB3qZJCNjgy9yBW53mRfX3zH0Xr1DslY'
                }
            };
            
            axios
            .request(moviesUrl)
            .then(function (response) {
                console.log(response.data.results);
                store.movies = response.data.results;
            })
            .catch(function (error) {
                console.error(error);
            });

            // series
            const seriesUrl = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/search/tv',
                params: { query: `${store.searchTitle}`, 
                include_adult: 'false', 
                language: 'en-US', 
                page: '1',
                api_key: '07817ee9ac4818e99a782b133fd5bf38' 
            },
                headers: {
                    accept: 'application/json',
                    // Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIwNzgxN2VlOWFjNDgxOGU5OWE3ODJiMTMzZmQ1YmYzOCIsInN1YiI6IjY1NmRiZmU5NGE0YmY2MDBjNTAzNTIwOCIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.RQk5iEa9mbLnB3qZJCNjgy9yBW53mRfX3zH0Xr1DslY'
                }
            };

            axios
            .request(seriesUrl)
            .then(function (response) {
                console.log(response.data.results);
                store.series = response.data.results;
            })
            .catch(function (error) {
                console.error(error);
            });
        }
    }
}
</script>

<template>
    <header class="bg-dark text-danger d-flex align-items-center">
        <AppHeader @search="getContents()" />
    </header>

    <vue-flip :active-hover="true" width="200px" height="50px">
          <template v-slot:front class="front">
            front
          </template>
          <template v-slot:back class="back">
            back
          </template>
        </vue-flip>

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
}

main {
    height: calc(100% - 6rem);
    background-color: black;
}
</style>
