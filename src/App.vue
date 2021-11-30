
/**
1. stampare tutti i dischi
2. passare i parametri di ogni singolo disco al figlio
3. al cambio della select in jeader effettuare il filter in main
4. generare dinamicamente la select in base ai generi presenti in main


 */


<template>
    <div id="app">


        <!-- 
            @changeGenre viene attivato al cambio della select
            genresList è la lista che arriva da @genresListed
         -->
        <Header @changeGenre="selectionGenre" :genresList="genres"  />

        <!-- 
            @genresListed viene attivato quando arriva il dato in axios
            genreToSearch è il dato che arriva da @changeGenre
         -->
        <Main :genreToSearch="genreSelected" @genresListed="genresToPops"  />

    </div>
</template>

<script>
import Header from "./components/Header";
import Main from "./components/Main";

export default {
    name: "App",
    components: {
        Header,
        Main,
    },
    data() {
        return {
            genreSelected:'',
            genres: []
        };
    },
    methods: {
        // chiamato da @changeGenre e salvo il genere selezionato
        selectionGenre(genre){
            this.genreSelected = genre;
        },

        // chiamato da @genresListed e salvo i generi per la select       
        genresToPops(arrGenres){
            console.log(arrGenres);
            this.genres = arrGenres;
        }
    },
};
</script>

<style lang="scss">
@import "./assets/styles/general";
</style>
