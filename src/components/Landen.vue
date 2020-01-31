<template>
    <div class="container">
        <div v-bind:key="land.id" v-for="land in landen" class="land">
            <Land v-bind:land="land" v-on:verwijder-land="$emit('verwijder-land', land.id)"/>
        </div>
    </div>
</template>

<script>
import Land from './Land';

export default {
    name: "Landen",
    components: {
        Land
    },
    props: ["landen"]
}
</script>

<style scoped>
    .land {
        width: 300px;
        margin: 0 auto;
    }
    .container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(350px, 400px));
        grid-row-gap: 3em;
        margin-bottom: 3em;
    }
</style>