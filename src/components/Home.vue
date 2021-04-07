<template>
  <div class="home-page">
       <div class="row initial-select">
            <div class="col-6 front-page-class">
                <button v-on:click="openNewPage('allClasses')" type="button" class="btn btn-primary btn-lg front-page-class-button" >Class</button> 
            </div>
            <div class="col-6 front-page-race">
                <button v-on:click="openNewPage('allRaces')" type="button" class="btn btn-primary btn-lg front-page-race-button" >Race</button>
            </div>
        </div>
  </div>
</template>
<script>
  export default {
      name: 'Home',
      props: {
          homePageChanger: String,
      },
      data(){
          return {
            pageChanger: this.homePageChanger,
          }
      },
      methods: {
        openNewPage(differentOption){
            this.$emit('changePage', differentOption);
        },
      }
  }
</script>
<style>
    @import "../../node_modules/bootstrap/dist/css/bootstrap.min.css";
    @import '../assets/main.css';
    @import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Stencil+Display:wght@500&family=Fondamento&display=swap');
</style>