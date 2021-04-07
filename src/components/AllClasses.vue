<template>
  <div class="all-classes">
        <div class="row">
          <div class= 'container classes-container'>
            <div class="col-12">
              <div class="row all-classes-page-title">
                  <h1 class="dnd-classes-title">Classes</h1>
              </div>
              <div class="row all-classes-page-thumbnails">
                  <div v-for="dndClass in allClasses" :key="dndClass.name" class="figure col-sx-12 col-sm-6 col-lg-3">
                    <div class="row justify-content-center">
                      <img :src="dndClass.image" class="figure-img img-fluid rounded img-classes-thumbnails" alt="A generic square placeholder image with rounded corners in a figure.">
                    </div>
                    <div class="row justify-content-center">
                      <button v-on:click="openNewPage(dndClass.name)" type="button" class="btn btn-primary all-classes-btn" data-toggle="button" aria-pressed="false" autocomplete="off">{{dndClass.name}}</button>
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
      name: 'AllClasses',
      props: {
        allClassesPageChanger: String,
        allClassesAllClasses: Object
      },
      data(){
        return {
          pageChanger: this.allClassesPageChanger,
          allClasses: this.allClassesAllClasses,
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