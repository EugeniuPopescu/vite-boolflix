<script>
import { store } from "../store.js"

export default {
    name: 'AppHeader',
    components: {
        
    },
    data() {
        return {
			store
        }
    },
	mounted() {
		console.log('Creato AppHeader');
	},
    methods: {
        search() {
            console.log("Cerca: ", this.store.searchTitle);
            this.$emit("search");
        }
    },
}
</script>

<template>
    <div class="container-fluid">
        <div class="row">
			<!-- title -->
            <div class="col-6">
                <h1>Boolflix</h1>
            </div>
            <div class="col-6 d-flex align-items-center">
				<!-- search input -->
                <div class="input-group">
                    <input v-model="store.searchTitle" @keyup.enter="$emit('search')"
					type="text" class="form-control" placeholder="Search in Boolflix..." aria-label="Recipient's username" aria-describedby="button-addon2">
                    <button @click="search"
					class="btn btn-outline-danger" type="button" id="button-addon2">Search</button>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
h1 {
    font-family: 'Silkscreen', sans-serif;
    font-size: 5rem;
}
</style>
