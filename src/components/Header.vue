<template>
    <header class="d-flex justify-content-between ps-3 pe-3">
        <div>
            <img src="../assets/img/spotify-logo.png" alt="Spotify" />
        </div>
        <div>
            <!-- $emit viene scatenato al cambio della select -->
            <select
            v-model="genre"
            @change="$emit('changeGenre',genre)"
             class="form-select mt-3" >
                <option value="" selected>Seleziona un genere</option>
                <option
                    v-for="(genre, index) in genresList"
                    :key="index"
                 :value="genre">{{genre}}</option>

            </select>
        </div>
    </header>
</template>

<script>
export default {
    name: "Haeder",
    props: {
      genresList: Array
    },
    data() {
        return {
            genre: ''
        };
    },
    methods: {},
};
</script>

<style lang="scss" scoped>
header {
    height: 70px;
    background-color: #2e3a46;
    line-height: 70px;
    img {
        width: 50px;
    }
}
</style>