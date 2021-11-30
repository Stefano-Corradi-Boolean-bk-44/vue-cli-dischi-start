<template>
    <div class="disc p-3 text-center">
        <div class="p-3">
            <img class="img-fluid mb-3" :src="discData.poster" :alt="discData.title" />
            <p class="title text-uppercase fw-bold">{{discData.title}}</p>
            <p class="author lead mb-0">{{discData.author}}</p>
            <p class="year">{{discData.year}}</p>
        </div>
    </div>  
</template>

<script>
export default {
    name: "Disc",
    props: {
        discData: Object
    },
};
</script>

<style lang="scss" scoped>
.disc {
    flex-basis: calc(100% / 5);

    div {
        background-color: #2e3a46;
        height: 100%;
    }

    .author,
    .year {
        color: #7d7977;
    }
}
</style>