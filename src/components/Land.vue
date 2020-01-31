<template>
    <div class="land" v-bind:style="{ background: land.url }">
        <button class="btn" v-on:click="landIsBezocht"><i class="fa fa-check-circle fa-3x"></i></button>
        <div class="niet-bezocht" v-bind:class="{'is-bezocht':land.bezocht}">
            <i class="fa fa-check-circle"></i>
        </div>
        <div>
            <h2 class="land-naam">{{land.naam}}</h2>
            <p class="land-steden">{{land.steden}}</p>
        </div>
        <button class="btn" v-on:click="$emit('verwijder-land', land.id)"><i class="fa fa-times-circle fa-3x"></i></button>
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
        background-size: cover !important;
        background-repeat: no-repeat !important;
        width: 300px;
        height: 200px;
        position: relative;
        text-align: right;
        padding: 1em;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: flex-end;
    }

    .niet-bezocht {
        display: flex;
        opacity: 0;
        position: absolute;
        width: 100%;
        height: 100%;
        transform: translate(1em,-1em);
        background-color: transparent;
        transition: background-color 1s;
    }

    .niet-bezocht i {
        position: relative;
        z-index: 101;
        font-size: 10em;
        color: limegreen;
    }

    .is-bezocht {
        justify-content: center;
        align-items: center;
        transition: background-color 1s;
        background-color: rgba(255,255,255,.8);
        animation: display 1200ms forwards;
    }

    .is-bezocht i {
        animation: spincheck 1500ms;
        transform: scale(1)
    }

    .btn {
        width: 33px;
        background-color: transparent;
        border: none;
        outline: none;
        cursor: pointer;
        text-align: center;
        position: relative;
        z-index: 100;
    }

    .btn:first-of-type {
        color: limegreen;
    }

    .btn:first-of-type:hover {
        animation: spin 800ms;
    }

    .btn:last-of-type {
        color: red;
    }

    .btn:last-of-type:hover {
        animation: shake 600ms;
    }

    @keyframes spin {
        from{transform: rotate(0)}
        to{transform: rotate(-720deg)}
    }

    @keyframes display {
        from{opacity: 0;}
        to{opacity: 1;}
    }

    @keyframes shake {
        0%{transform: translateX(0)}
        20%{transform: translateX(-2px)}
        40%{transform: translateX(2px)}
        60%{transform: translateX(-2px)}
        80%{transform: translateX(2px)}
        100%{transform: translateX(0)}
    }

    @keyframes spincheck {
        0%{transform: rotateY(360deg) scale(1.5);}
        100%{transform: rotateY(720deg) scale(1);}
    }
</style>