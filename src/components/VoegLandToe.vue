<template>
    <div>
        <form v-on:submit="VoegToe">
            <input type="text" v-model="naam" name="naam" placeholder="Naam land">
            <input type="text" v-model="steden" name="steden" placeholder="Stad/Steden">
            <input type="text" v-model="url" name="url" placeholder="Url foto">
            <input type="submit" value="Voeg toe" class="voeg-toe-knop">
        </form>
    </div>
</template>

<script>
import uuid from 'uuid';
export default {
    name: "VoegLandToe",
    data() {
        return {
            naam: '',
            steden: '',
            url: ''
        }
    },
    methods: {
        VoegToe(e) {
            e.preventDefault();
            const nieuwLand = {
                id: uuid.v4(),
                naam: this.naam,
                steden: this.steden,
                url: this.url,
                bezocht: false
            }

            this.$emit('voeg-toe', nieuwLand);

            this.naam = '';
            this.steden = '';
            this.url = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
        flex-direction: column;
        width: 300px;
    }
</style>