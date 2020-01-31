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
          url: "linear-gradient(to right, rgba(255,255,255,0), rgba(255,255,255,.1) 20%, rgba(255,255,255,.6) 50%, rgba(255,255,255,.9)), url('https://www.fourseasons.com/alt/img-opt/~70.1530.0,0000-28,2500-2616,0000-1471,5000/publish/content/dam/fourseasons/images/web/SYD/SYD_156_original.jpg')",
          bezocht: false
        },
        {
          id: 2,
          naam: "IJsland",
          steden: "Reykjavik",
          url: "linear-gradient(to right, rgba(255,255,255,0), rgba(255,255,255,.1) 20%, rgba(255,255,255,.6) 50%, rgba(255,255,255,.9)), url('https://upload.wikimedia.org/wikipedia/commons/thumb/d/d6/Reykjav%C3%ADk_s%C3%A9%C3%B0_%C3%BAr_Hallgr%C3%ADmskirkju.jpeg/1200px-Reykjav%C3%ADk_s%C3%A9%C3%B0_%C3%BAr_Hallgr%C3%ADmskirkju.jpeg')",
          bezocht: false
        },
        {
          id: 3,
          naam: "Engeland",
          steden: "London",
          url: "linear-gradient(to right, rgba(255,255,255,0), rgba(255,255,255,.1) 20%, rgba(255,255,255,.6) 50%, rgba(255,255,255,.9)), url('https://www.clinkhostels.com/wp-content/uploads/2015/03/london22.jpg')",
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
  box-sizing: border-box;
}

.fa {
  font-family: "FontAwesome";
}
</style>
