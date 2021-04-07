<template>
  <div class="race-page">
      <div class="row">
          <div class="container">
              <div class="row">
                  <div class="col-8 races-main-description">
                      <div class="row justify-content-start introduction-to-race">
                        <div class="col-12">
                          <h1 class="race-title-on-race-page">{{allRaces[pageChanger].name}}</h1>
                          <p class="race-mini-description-on-race-page">{{allRaces[pageChanger].introduction}}</p>
                        </div>
                      </div>
                      <div class="row justify-content-start race-detailed-description">
                        <div class="col-12">
                          <h2 class="race-detailed-description-title">{{allRaces[pageChanger].name}} Features</h2>
                              <p>
                              <strong>Age:</strong>
                              {{allRaces[pageChanger].age}}
                              <br>
                              <strong>Alignment:</strong>
                              {{allRaces[pageChanger].alignment}}
                              <br>
                              <strong>Size:</strong>
                              {{allRaces[pageChanger].size}}
                              <br>
                              <strong>Speed:</strong>
                              {{allRaces[pageChanger].speed}}
                              <br>
                              <strong>Languages:</strong>
                              {{allRaces[pageChanger].languages}}
                              <br>
                              </p>
                          <h5 class="race-detailed-description-mini-title">Ability Score Increase: {{allRaces[pageChanger].abilityScoreIncrease}}</h5>
                        </div>
                      </div>
                      <div class="row justify-content-start" style="margin-left: 2px">
                          <button v-on:click="finalChoiceOfRace(allRaces[pageChanger].name)" type="button" class="btn btn-primary btn-lg recommendations choose-race-btn" data-toggle="button" aria-pressed="false" autocomplete="off" style="margin-top: 15px">
                              Choose {{allRaces[pageChanger].name}}
                          </button>
                    </div>
                  </div>  
                  <div class="col-3 races-sidebar-recommendations">
                    <div class="row justify-content-around">
                      <div class="col-12 justify-content-around">
                        <div class="row justify-content-around">
                          <h3 class="similar-races">Similar Races</h3>
                        </div>
                        <div class="row justify-content-center">
                          <h4 class="similar-races-example">{{allRaces[pageChanger].similarRaces.firstName}}</h4>
                        </div>
                          <h5 class="similar-races-example-description">
                          <h5 class="similarities-and-race-bonuses">Similarities:</h5>{{allRaces[pageChanger].similarRaces.firstDescription}}
                          </h5>
                          <div class="row justify-content-around">
                            <button v-on:click="openNewPage(allRaces[pageChanger].similarRaces.firstName)" type="button" class="btn btn-primary recommendations race-or-class-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                            {{allRaces[pageChanger].similarRaces.firstName}}
                            </button>
                          </div>
                          <div class="row justify-content-center">
                            <h4 class="similar-races-example">{{allRaces[pageChanger].similarRaces.secondName}}</h4>
                          </div>
                          <h5 class="similar-races-example-description">
                          <h5 class="similarities-and-race-bonuses">Similarities:</h5>{{allRaces[pageChanger].similarRaces.secondDescription}}
                          </h5>
                          <div class="row justify-content-around">
                            <button v-on:click="openNewPage(allRaces[pageChanger].similarRaces.secondName)" type="button" class="btn btn-primary recommendations race-or-class-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                            {{allRaces[pageChanger].similarRaces.secondName}}
                            </button>
                          </div>
                          <div class="row justify-content-around">
                            <h3 class="suitable-classes">Suitable Classes</h3>
                          </div>
                          <div class="row justify-content-center">
                            <h4 class="suitable-classes-example">{{allRaces[pageChanger].suitableClasses.firstName}}</h4>
                          </div>
                          <h5 class="suitable-classes-example-description">
                          <h5 class="similarities-and-race-bonuses">Primary Ability:</h5>{{allRaces[pageChanger].suitableClasses.firstDescription}}
                          </h5>
                          <div class="row justify-content-around">
                            <button v-on:click="openNewPage(allRaces[pageChanger].suitableClasses.firstName)" type="button" class="btn btn-primary recommendations race-or-class-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                            {{allRaces[pageChanger].suitableClasses.firstName}}
                            </button>
                          </div>
                          <div class="row justify-content-center">
                            <h4 class="suitable-classes-example">{{allRaces[pageChanger].suitableClasses.secondName}}</h4>
                          </div>
                          <h5 class="suitable-classes-example-description">
                          <h5 class="similarities-and-race-bonuses">Primary Ability:</h5>{{allRaces[pageChanger].suitableClasses.secondDescription}}
                          </h5>
                          <div class="row justify-content-around">
                            <button v-on:click="openNewPage(allRaces[pageChanger].suitableClasses.secondName)" type="button" class="btn btn-primary recommendations race-or-class-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                            {{allRaces[pageChanger].suitableClasses.secondName}}
                            </button>
                          </div>
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
      name: 'RacePage',
      props: {
          racePagePageChanger: String,
          racePageFinalRace: String,
          racePageAllRaces: Object
      },
      data(){
          return {
              pageChanger: this.racePagePageChanger,
              finalRace: this.racePageFinalRace,
              allRaces: this.racePageAllRaces,
          }
      },
      methods: {
        openNewPage(differentOption){
            this.$emit('changePage', differentOption);
        },
        finalChoiceOfRace(finalRace){
          if(this.allRaces['Half-Elf'].halfElfExtraAttrs.length !== 0){
              this.allRaces['Half-Elf'].halfElfExtraAttrs = [];
          }
          this.$emit('clearHalfElfAttrs', this.allRaces['Half-Elf'].halfElfExtraAttrs);
          this.$emit('newFinalRace', finalRace);
        },
      }
  }
</script>
<style>
    @import "../../node_modules/bootstrap/dist/css/bootstrap.min.css";
    @import '../assets/main.css';
    @import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Stencil+Display:wght@500&family=Fondamento&display=swap');
</style>