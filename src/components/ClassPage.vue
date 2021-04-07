<template>
  <div class="class-page">
      <div class="row">
          <div class="container">
              <div class="row">
                  <div class="col-8 classes-main-description">
                  <div class="introduction-to-class">
                      <h1 class="class-title-on-class-page">{{allClasses[pageChanger].name}}</h1>
                      <p class="class-mini-description-on-class-page">{{allClasses[pageChanger].introduction}}</p>
                  </div>
                  <div class="row class-info">
                    <div class="col-12 ">
                      <div class="row">
                        <p class="scroller-warning">*Scroll right if you can't see the full table</p>
                        <div class="table-scroller">
                        <table class="table dnd-class-table">
                            <thead class="thead-dark header-of-class-table">
                            <tr>
                                <th scope="col" :colspan=allClasses[pageChanger].colspanBeforeSlots style='text-align: start'>The {{allClasses[pageChanger].name}}</th>
                                <th class="spell-slots" v-if="allClasses[pageChanger].type == 'Spellcaster' || allClasses[pageChanger].type == 'halfSpellcaster'" scope="col" :colspan=allClasses[pageChanger].colspanSlots >Spell Slots per Spell Level</th>
                                <th v-else scope="col" colspan=11 style="padding-left: 3%;"></th>
                            </tr>
                            <tr class="thead-dark secondary-header-of-class-table">
                                <th>Level</th>
                                <template v-for="(item, index) in allClasses[pageChanger].levels[1]"> 
                                    <template v-if="index === 'spellSlots'">
                                    <template v-for="(slot, slotIndex) in item">
                                        <th v-bind:key="slotIndex">{{writeIndexAsTitleOfSlot(slotIndex)}}</th>
                                    </template>
                                </template>
                                <template v-else>
                                    <th v-bind:key="item.feature">{{makeReadable(index)}}</th>
                                </template>
                                </template>
                            </tr>
                            </thead>
                            <tbody>
                            <tr v-for="(levelFeatures, levelNumber) in allClasses[pageChanger].levels" v-bind:key="levelNumber">                         
                                <td>{{levelNumber}}</td>
                                <template v-for="(value, index) in levelFeatures"> 
                                <template v-if="index === 'spellSlots'">
                                    <template v-for="(slot, slotIndex) in value">
                                    <th v-bind:key="slotIndex">{{slot}}</th>
                                    </template>
                                </template>
                                <template v-else>
                                    <td v-bind:key="index">{{value}}</td>
                                </template>
                                </template>
                            </tr>                      
                            </tbody>
                        </table>
                        </div>
                      </div>
                      <div class="row">
                        <div class="class-detailed-description">
                            <h1 class="class-detailed-description-title">Class Features</h1>
                            <h5 class="class-detailed-description-mini-title">Hit Points</h5>
                            <p>
                                <strong>Hit Dice:</strong>
                                {{allClasses[pageChanger].hitPoints.hitDice}}
                                <br>
                                <strong>Hit Points at 1st Level:</strong>
                                {{allClasses[pageChanger].hitPoints.hitPointsAtFirstLevel}}
                                <br>
                                <strong>Hit Points at Higher Levels:</strong>
                                {{allClasses[pageChanger].hitPoints.hitPointsAtHigherLevels}}
                                <br>
                            </p>
                            <h5 class="class-detailed-description-mini-title">Proficiencies</h5>
                            <p>
                                <strong>Armor:</strong>
                                {{allClasses[pageChanger].proficiencies.armor}}
                                <br>
                                <strong>Weapons:</strong>
                                {{allClasses[pageChanger].proficiencies.weapons}}
                                <br>
                                <strong>Tools:</strong>
                                {{allClasses[pageChanger].proficiencies.tools}}
                                <br>
                                <strong>Saving Throws:</strong>
                                {{allClasses[pageChanger].proficiencies.savingThrows}}
                                <br>
                                <strong>Skills:</strong>
                                {{allClasses[pageChanger].proficiencies.skills}}
                                <br>
                            </p>
                            <button v-on:click="finalChoiceOfClass(allClasses[pageChanger].name)" type="button" class="btn btn-primary btn-lg recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">
                                Choose {{allClasses[pageChanger].name}}
                            </button>
                        </div>
                      </div>
                    </div>
                  </div>  
                  </div>
                  <div class="col-3 classes-sidebar-recommendations">
                    <div class="row justify-content-center">
                      <div class="col-12">
                        <div class="row justify-content-around">
                          <h3 class="similar-classes">Similar Classes</h3>
                        </div>
                        <div class="row justify-content-center">
                          <h4 class="similar-classes-example">{{allClasses[pageChanger].similarClasses.firstName}}</h4>
                          <h5 class="similar-classes-example-description">
                          <h5 class="similarities-and-race-bonuses">Similarities:</h5>{{allClasses[pageChanger].similarClasses.firstDescription}}
                          </h5>
                        </div>
                        <div class="row justify-content-around">
                          <button v-on:click="openNewPage(allClasses[pageChanger].similarClasses.firstName)" type="button" class="btn btn-primary recommendations race-or-class-btn" data-toggle="button" aria-pressed="false" autocomplete="off">{{allClasses[pageChanger].similarClasses.firstName}}</button>
                        </div>
                        <div class="row justify-content-center">
                          <h4 class="similar-classes-example">{{allClasses[pageChanger].similarClasses.secondName}}</h4>
                          <h5 class="similar-classes-example-description">
                          <h5 class="similarities-and-race-bonuses">Similarities:</h5>{{allClasses[pageChanger].similarClasses.secondDescription}}
                          </h5>
                         </div>
                        <div class="row justify-content-around">
                          <button v-on:click="openNewPage(allClasses[pageChanger].similarClasses.secondName)" type="button" class="btn btn-primary recommendations race-or-class-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                          {{allClasses[pageChanger].similarClasses.secondName}}
                          </button>
                        </div>
                        <div class="row justify-content-around">
                          <h3 class="suitable-races">Suitable Races</h3>
                        </div>
                        <div class="row justify-content-center">
                          <h4 class="suitable-races-example">{{allClasses[pageChanger].suitableRaces.firstName}}</h4>
                        </div>
                          <h5 class="suitable-races-example-description">
                          <h5 class="similarities-and-race-bonuses">Race Bonuses:</h5>{{allClasses[pageChanger].suitableRaces.firstDescription}}
                          </h5>
                        <div class="row justify-content-around">
                          <button v-on:click="openNewPage(allClasses[pageChanger].suitableRaces.firstName)" type="button" class="btn btn-primary recommendations race-or-class-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                          {{allClasses[pageChanger].suitableRaces.firstName}}
                          </button>
                        </div>
                        <div class="row justify-content-center">
                          <h4 class="suitable-races-example">{{allClasses[pageChanger].suitableRaces.secondName}}</h4>
                        </div>
                          <h5 class="suitable-races-example-description">
                          <h5 class="similarities-and-race-bonuses">Race Bonuses:</h5>{{allClasses[pageChanger].suitableRaces.secondDescription}}
                          </h5>
                        <div class="row justify-content-around">
                          <button v-on:click="openNewPage(allClasses[pageChanger].suitableRaces.secondName)" type="button" class="btn btn-primary recommendations race-or-class-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                          {{allClasses[pageChanger].suitableRaces.secondName}}
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
        classPagePageChanger: String,
        classPageFinalClass: String,
        classPageAllClasses: Object,
        classPageAllRaces: Object
        // characterSavingThrowsBonuses: Array
      },
      data(){
        return {
          pageChanger: this.classPagePageChanger,
          finalClass: this.classPageFinalClass,
          allClasses: this.classPageAllClasses,
          allRaces: this.classPageAllRaces,
          // characterSavingThrowsBonuses: this.characterSavingThrowsBonuses
        }
      },
      methods: {
        makeReadable(oneWord){
          let result1 = '';
          let result2 = '';
          let finalWords = '';

          oneWord = oneWord.split('');
          oneWord[0] = oneWord[0].toUpperCase();
          for(let i=1; i < oneWord.length; i++){
              if (oneWord[i] == oneWord[i].toUpperCase()){
                  result1 = oneWord.slice(0, i).join('');
                  result2 = oneWord.slice(i).join('');
                  finalWords = result1 + ' ' + result2;
              }
          }
          if(finalWords == ''){
          finalWords = oneWord.join('');
          }
              return finalWords;
        },
        writeIndexAsTitleOfSlot(index){
          let result;
            if(index == 0){
              result = index + 1 + 'st';
            }
            else if(index == 1){
              result = index + 1 + 'nd';
            }
            else if(index == 2){
              result = index + 1 + 'rd';
            }
            else{
              result = index + 1 + 'th';
            }
          return result;
        }, 
        openNewPage(differentOption){
          this.$emit('changePage', differentOption);
        },
        finalChoiceOfClass(finalClassName){
          if(this.allRaces['Half-Elf'].halfElfExtraAttrs.length !== 0){
              this.allRaces['Half-Elf'].halfElfExtraAttrs = [];
          }
          this.$emit('clearHalfElfAttrs', this.allRaces['Half-Elf'].halfElfExtraAttrs);
          this.$emit('newFinalClass', finalClassName);
        },
      }
  }
</script>
<style>
    @import "../../node_modules/bootstrap/dist/css/bootstrap.min.css";
    @import '../assets/main.css';
    @import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Stencil+Display:wght@500&family=Fondamento&display=swap');
</style>