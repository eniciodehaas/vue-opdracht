<template>
  <div id="app">
    <Header />
    <Landen v-bind:landen="landen" v-on:verwijder-land="verwijderLand"/>
    <VoegLandToe v-on:voeg-toe="voegLandToe"/>
  </div>
</template>

<script>
import Header from './components/layout/Header'
import Landen from './components/Landen'
import VoegLandToe from './components/VoegLandToe'

export default {
  name: 'app',
  components: {
    Header,
    Landen,
    VoegLandToe
  },
  data() {
    return {
      landen: [
        {
          id: 1,
          naam: "Australië",
          steden: "Sydney",
          url: "",
          bezocht: false
        },
        {
          id: 2,
          naam: "IJsland",
          steden: "Reykjavik",
          url: "",
          bezocht: true
        },
        {
          id: 3,
          naam: "Engeland",
          steden: "London",
          url: "",
          bezocht: false
        }
      ]
    }
  },
  methods: {
    verwijderLand(id) {
      this.landen = this.landen.filter(land => land.id !== id);
    },
    voegLandToe(nieuwLand) {
      this.landen = [...this.landen, nieuwLand];
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  font-family: 'Comfortaa', cursive;
}

.fa {
  font-family: "FontAwesome";
}
</style>
