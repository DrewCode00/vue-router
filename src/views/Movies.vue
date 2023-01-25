<script setup >
import {ref, onMounted} from 'vue';
import MovieCard from '../components/MoviesCard.vue'

const movieList = ref([]);

const isLoading = ref(true);

onMounted(async() => {
    const result = await fetch('http://localhost:3000/movies')
    const response = await result.json();
    fetch('http://localhost:3000/movies')
    movieList.value = response;
    isLoading.value = false;

})
</script> 

<template>

<div class="grid grid-cols-3 gap-4" >
    <h1>Movies</h1>
    <div class="max-w-sm mx-auto" v-if="isLoading">
        <span class="text-2xl font-bold text-indigo-700">Is Loading...</span>
    </div>
    <MovieCard v-for="movie in movieList" :key="movie.id" :movie="movie"/>
</div>
</template>

