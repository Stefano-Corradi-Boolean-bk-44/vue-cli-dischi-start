<template>
    <main class="container mt-5">
        <div class="d-flex flex-wrap">
            <!-- il ciclo non lo faccio dall'array dei data ma dalla computed che fa il filtro -->
            <Disc
                v-for="(disc, index) in filteredDiscs"
                :key="index"
                :discData="disc"
              />

        </div>
    </main>
</template>

<script>
import axios from "axios";
import Disc from "./Disc";

export default {
    name: "Main",
    components: {
        Disc,
    },
    props: {
        genreToSearch: String
    },
    computed: {
        filteredDiscs(){
            // se non seleziono nulla restituisco l'array completo dei dischi
            if(this.genreToSearch === ''){
                return this.discs;
            }

            // se arriva dalla props genreToSearch un dato effettuo il filtro
            
            // filter compatto
            //return this.discs.filter(disc => disc.genre === this.genreToSearch);


            //filter esteso con filter
           /*        = this.discs.filter( disc => {
                return disc.genre === this.genreToSearch 
            } )*/

            //filter esteso con forEach
            const discFiltered= [];
            this.discs.forEach( disc => {
                if(disc.genre === this.genreToSearch){
                    discFiltered.push(disc)
                }
            })

            return discFiltered;
        }
    },
    data() {
        return {    
            discs: [],
            genres: []
        };
    },
    created() {

        axios
            .get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((res) => {
                // popolo l'array dei dischi
                this.discs = res.data.response;
                
                // popolo l'array dei generi
                this.discs.forEach(disc => {
                    // effettuo il push solo se il genere non è presente
                    if(!this.genres.includes(disc.genre)){
                        this.genres.push(disc.genre)
                    }
                })

                // una volta popolato l'array dei generi scateno l'$emit
                this.$emit('genresListed',this.genres)

            })
            .catch((err) => {
                console.log(err);
            });
    },
};
</script>