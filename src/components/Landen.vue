<template>
    <div>
        <div v-bind:key="land.id" v-for="land in landen">
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
    
</style>