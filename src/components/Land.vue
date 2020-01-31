<template>
    <div class="land">
        <button v-on:click="landIsBezocht"><i class="fa fa-check-circle fa-2x"></i></button>
        <div class="niet-bezocht" v-bind:class="{'is-bezocht':land.bezocht}">
            <i class="fa fa-check-circle"></i>
        </div>
        <p>{{land.naam}}</p>
        <button class="verwijder" v-on:click="$emit('verwijder-land', land.id)"><i class="fa fa-times-circle fa-2x"></i></button>
    </div>
</template>

<script>
export default {
    name: "Land",
    props: ["land"],
    methods: {
        landIsBezocht() {
            this.land.bezocht = !this.land.bezocht;
        }
    }
}
</script>

<style scoped>
    .land {
        display: flex;
    }

    .niet-bezocht {
        display: none;
    }

    .is-bezocht {
        display: block
    }
</style>