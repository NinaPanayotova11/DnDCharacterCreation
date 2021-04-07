<template>
  <!-- <nav class="navbar navbar-expand-md bg-dark navbar-dark">
    <a class="navbar-brand" v-on:click="pageChanger = openNewPage('home')">DnD Character Creation</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#collapsibleNavbar">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="collapsibleNavbar">
      <ul class="navbar-nav">
        <li class="nav-item">
          <a class="nav-link" v-on:click="pageChanger = openNewPage('home')">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" v-on:click="pageChanger = openNewPage('allClasses')">Class</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" v-on:click="pageChanger = openNewPage('allRaces')">Race</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" v-on:click="pageChanger = openNewPage('calc')">Calculate Ability Scores</a>
        </li>
      </ul>
    </div>  
  </nav> -->
   <nav class="navbar navbar-expand-md navbar-dark bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand" v-on:click="pageChanger = openNewPage('home')">DnD Character Creation</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav ml-auto">
        <li class="nav-item">
          <a class="nav-link"  v-on:click="pageChanger = openNewPage('home')">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link"  v-on:click="pageChanger = openNewPage('allClasses')">Class</a>
        </li>
        <li class="nav-item">
          <a class="nav-link"  v-on:click="pageChanger = openNewPage('allRaces')">Race</a>
        </li>
        <li class="nav-item">
          <a class="nav-link"  v-on:click="pageChanger = openNewPage('calc')">Calculate Ability Scores</a>
        </li>
      </ul>
    </div>
  </div>
</nav>
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
        openNewPage(differentOption){
          this.$emit('changePage', differentOption);
        }
    }
}
</script>
<style>
@import "../../node_modules/bootstrap/dist/css/bootstrap.min.css";
@import '../assets/main.css';
@import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Stencil+Display:wght@500&family=Fondamento&display=swap');
</style>