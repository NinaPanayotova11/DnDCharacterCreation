<template>
    <div class= "row">
        <div class="col-12">
          <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
              <ul class="navbar-nav">
                <li class="nav-item active">
                  <a class="nav-link nav-brand" v-on:click="pageChanger = openHomePage()">DnD Character Creation </a>
                </li>
                <li class="nav-item active">
                  <a class="nav-link" v-on:click="pageChanger = openHomePage()">Home </a>
                </li>
                <li class="nav-item active">
                  <a class="nav-link" v-on:click="pageChanger = openPageClasses()">Classes </a>
                </li>
                <li class="nav-item active">
                  <a class="nav-link" v-on:click="pageChanger = openPageRaces()">Races </a>
                </li>
                <template v-if="finalClass !== ''">
                  <li>
                    <h2 class="navbar-final-class">{{finalClass}}</h2>
                  </li>
                </template>
                <template v-if="finalRace !== ''">
                  <li>
                    <h2 class="navbar-final-race">{{finalRace}}</h2>
                  </li>
                </template>
                <template v-if="finalRace !== '' && finalClass !== ''">
                  <li>
                    <button v-on:click="pageChanger = openPageCalc()" type="button" class="btn btn-primary btn-lg recommendations navbar-calc-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                      Calculate Ability Scores
                    </button>
                  </li>
                </template>
              </ul>
          </nav>
        </div>
      </div>
</template>
<script>
export default {
    name: 'NavBar',
    props: {
        navBarPageChanger: String,
        navBarFinalClass: String,
        navBarFinalRace: String,
    },
    data () {
        return {
            finalClass: this.navBarFinalClass,
            finalRace: this.navBarFinalRace,
            pageChanger: this.navBarPageChanger
        }
    },
    watch: {
        navBarFinalClass: function (newClass) {
            this.finalClass = newClass;
        },
        navBarFinalRace: function (newRace) {
            this.finalRace = newRace;
        },
        navBarPageChanger: function (newPage) {
            this.pageChanger = newPage;
        },
    },
    methods: {
        openPageCalc(){
            this.$emit('changePage', 'calc');
        },
        openPageClasses(){
            this.$emit('changePage', 'allClasses');
        },
        openPageRaces(){
            this.$emit('changePage', 'allRaces');
        },
        openHomePage(){
            this.$emit('changePage', 'home');
        }
    }
}
</script>
<style>
@import "../../node_modules/bootstrap/dist/css/bootstrap.min.css";
@import '../assets/main.css';
</style>