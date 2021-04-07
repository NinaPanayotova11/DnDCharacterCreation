<template>
  <div class="all-races">
    <div class="row">
      <div class="container races-container">
        <div class="col-12">
          <div class="row all-races-page-title">
            <h1 class="dnd-races-title">Races</h1>
          </div>
          <div class="row all-races-page-thumbnails">
            <div v-for="dndRace in allRaces" :key="dndRace.name" class="figure col-sx-12 col-sm-6 col-lg-3">
                <div class="row justify-content-center">
                <img :src="dndRace.image" class="figure-img img-fluid rounded img-classes-thumbnails" alt="A generic square placeholder image with rounded corners in a figure.">
              </div>
              <div class="row justify-content-center">
                <button v-on:click="openNewPage(dndRace.name)" type="button" class="btn btn-primary all-races-btn" data-toggle="button" aria-pressed="false" autocomplete="off">{{dndRace.name}}</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
      name: 'AllRaces',
      props: {
        allRacesPageChanger: String,
        allRacesAllRaces: Object
      },
      data(){
        return {
          pageChanger: this.allRacesPageChanger,
          allRaces: this.allRacesAllRaces,
        }
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