<template>
  <div id="app">
    <NavBar
        :navBarPageChanger="pageChanger"
        :navBarFinalClass="finalClass"
        :navBarFinalRace="finalRace"
        @changePage="getNewPageNavBar">
    </NavBar>
    <template v-if="pageChanger === 'home'"> 
        <div class="row initial-select">
            <div class="col-6 front-page-class">
                <button v-on:click="pageChanger = 'allClasses'" type="button" class="btn btn-primary btn-lg front-page-class-button" >Class</button> 
            </div>
            <div class="col-6 front-page-race">
                <button v-on:click="pageChanger = 'allRaces'" type="button" class="btn btn-primary btn-lg front-page-race-button" >Race</button>
            </div>
        </div>
    </template>
    <template v-if="pageChanger === 'allClasses'">
      <div class="all-classes">
        <div class="row">
          <div class= 'container classes-container'>
            <div class="col-12">
              <div class="row all-classes-page-title">
                  <h1 class="dnd-classes-title">Classes</h1>
              </div>
              <div class="row all-classes-page-thumbnails">
                  <div v-for="dndClass in allClasses" :key="dndClass.name" class="figure col-3">
                      <img :src="dndClass.image" class="figure-img img-fluid rounded img-classes-thumbnails" alt="A generic square placeholder image with rounded corners in a figure.">
                      <button v-on:click="chooseClass(dndClass.name)" type="button" class="btn btn-primary all-classes-btn" data-toggle="button" aria-pressed="false" autocomplete="off">{{dndClass.name}}</button>
                  </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </template>
    <template v-if="pageChanger === 'allRaces'">
      <div class="all-races">
        <div class="row">
          <div class="container races-container">
            <div class="col-12">
              <div class="row all-races-page-title">
                <h1 class="dnd-races-title">Races</h1>
              </div>
              <div class="row all-races-page-thumbnails">
                <div v-for="dndRace in allRaces" :key="dndRace.name" class="figure col-3">
                    <img :src="dndRace.image" class="figure-img img-fluid rounded img-classes-thumbnails" alt="A generic square placeholder image with rounded corners in a figure.">
                    <button v-on:click="chooseRace(dndRace.name)" type="button" class="btn btn-primary all-races-btn" data-toggle="button" aria-pressed="false" autocomplete="off">{{dndRace.name}}</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </template>
    <div v-for="name in Object.keys(allClasses)" v-bind:key="name">
     <template v-if="pageChanger === name">
        <div class="class-page">
            <div class="row">
                <div class="container">
                    <div class="row">
                        <div class="col-9 classes-main-description">
                        <div class="introduction-to-class">
                            <h1 class="class-title-on-class-page">{{allClasses[pageChanger].name}}</h1>
                            <p class="class-mini-description-on-class-page">{{allClasses[pageChanger].introduction}}</p>
                        </div>
                        <div class="row class-table">
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
                        <div class="col-3 classes-sidebar-recommendations">
                            <h3 class="similar-classes">Similar Classes</h3>
                            <h4 class="similar-classes-example">{{allClasses[pageChanger].similarClasses.firstName}}</h4>
                            <h5 class="similar-classes-example-description">
                            <strong>Similarities:</strong>{{allClasses[pageChanger].similarClasses.firstDescription}}
                            </h5>
                            <button v-on:click="chooseClass(allClasses[pageChanger].similarClasses.firstName)" type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">{{allClasses[pageChanger].similarClasses.firstName}}</button>
                            <h4 class="similar-classes-example">{{allClasses[pageChanger].similarClasses.secondName}}</h4>
                            <h5 class="similar-classes-example-description">
                            <strong>Similarities:</strong>{{allClasses[pageChanger].similarClasses.secondDescription}}
                            </h5>
                            <button v-on:click="chooseClass(allClasses[pageChanger].similarClasses.secondName)" type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">
                            {{allClasses[pageChanger].similarClasses.secondName}}
                            </button>
                            <h3 class="suitable-races">Suitable Races</h3>
                            <h4 class="suitable-races-example">{{allClasses[pageChanger].suitableRaces.firstName}}</h4>
                            <h5 class="suitable-races-example-description">
                            <strong>Race Bonuses:</strong>{{allClasses[pageChanger].suitableRaces.firstDescription}}
                            </h5>
                            <button v-on:click="chooseRace(allClasses[pageChanger].suitableRaces.firstName)" type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">
                            {{allClasses[pageChanger].suitableRaces.firstName}}
                            </button>
                            <h4 class="suitable-races-example">{{allClasses[pageChanger].suitableRaces.secondName}}</h4>
                            <h5 class="suitable-races-example-description">
                            <strong>Race Bonuses:</strong>{{allClasses[pageChanger].suitableRaces.secondDescription}}
                            </h5>
                            <button v-on:click="chooseRace(allClasses[pageChanger].suitableRaces.secondName)" type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">
                            {{allClasses[pageChanger].suitableRaces.secondName}}
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
      </template>
    </div>
    <div v-for="name in Object.keys(allRaces)" v-bind:key="name">
        <template v-if="pageChanger === name">
            <div class="race-page">
                <div class="row">
                    <div class="container">
                        <div class="row">
                            <div class="col-9 races-main-description">
                                <div class="introduction-to-race">
                                    <h1 class="race-title-on-race-page">{{allRaces[pageChanger].name}}</h1>
                                    <p class="race-mini-description-on-race-page">{{allRaces[pageChanger].introduction}}</p>
                                </div>
                                <div class="race-detailed-description">
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
                                    <button v-on:click="finalChoiceOfRace(allRaces[pageChanger].name)" type="button" class="btn btn-primary btn-lg recommendations choose-race-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                                        Choose {{allRaces[pageChanger].name}}
                                    </button>
                                </div>
                            </div>  
                            <div class="col-3 races-sidebar-recommendations">
                                <h3 class="similar-races">Similar Races</h3>
                                <h4 class="similar-races-example">{{allRaces[pageChanger].similarRaces.firstName}}</h4>
                                <h5 class="similar-races-example-description">
                                <strong>Similarities:</strong>{{allRaces[pageChanger].similarRaces.firstDescription}}
                                </h5>
                                <button v-on:click="chooseRace(allRaces[pageChanger].similarRaces.firstName)" type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">
                                {{allRaces[pageChanger].similarRaces.firstName}}
                                </button>
                                <h4 class="similar-races-example">{{allRaces[pageChanger].similarRaces.secondName}}</h4>
                                <h5 class="similar-races-example-description">
                                <strong>Similarities:</strong>{{allRaces[pageChanger].similarRaces.secondDescription}}
                                </h5>
                                <button v-on:click="chooseRace(allRaces[pageChanger].similarRaces.secondName)" type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">
                                {{allRaces[pageChanger].similarRaces.secondName}}
                                </button>
                                <h3 class="suitable-classes">Suitable Classes</h3>
                                <h4 class="suitable-classes-example">{{allRaces[pageChanger].suitableClasses.firstName}}</h4>
                                <h5 class="suitable-classes-example-description">
                                <strong>Primary Ability:</strong>{{allRaces[pageChanger].suitableClasses.firstDescription}}
                                </h5>
                                <button v-on:click="chooseClass(allRaces[pageChanger].suitableClasses.firstName)" type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">
                                {{allRaces[pageChanger].suitableClasses.firstName}}
                                </button>
                                <h4 class="suitable-classes-example">{{allRaces[pageChanger].suitableClasses.secondName}}</h4>
                                <h5 class="suitable-classes-example-description">
                                <strong>Primary Ability:</strong>{{allRaces[pageChanger].suitableClasses.secondDescription}}
                                </h5>
                                <button v-on:click="chooseClass(allRaces[pageChanger].suitableClasses.secondName)" type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">
                                {{allRaces[pageChanger].suitableClasses.secondName}}
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </template>
    </div>
    <template v-if="pageChanger === 'calc'">
        <AbilityCalculator 
            :calculatorRaces="allRaces" 
            :calculatorClasses="allClasses"  
            :calculatorPageChanger="pageChanger" 
            :calculatorFinalClass="finalClass" 
            :calculatorFinalRace="finalRace" 
            :calculatorCharacterName="characterName" 
            :calculatorAttributesModifiers="attributesModifiers" 
            :calculatorAttributesTotalScores="attributesTotalScores" 
            @changePageAbilityCalc="getNewPageAbilityCalc"
            @changeCharacterName="getNewCharName"
            @changeAttributesModifiers="getNewMods"
            @changeAttributesTotalScores="getNewTotal">
        </AbilityCalculator>
    </template>
    <template v-if="pageChanger === 'finishedSheet'">
        <FinishedSheet
            :finishedSheetFinalClass="finalClass"
            :finishedSheetFinalRace="finalRace"
            :finishedSheetCharacterName="characterName"
            :finishedSheetAttributesModifiers="attributesModifiers"
            :finishedSheetAttributesTotalScores="attributesTotalScores"
            :finishedSheetSavingThrows="savingThrows">
        </FinishedSheet>
    </template>
  </div>
</template>

<script>
import dndClassesData from './dndClassesData.json'
import dndRacesData from './dndRacesData.json'
import AbilityCalculator from './components/AbilityCalculator'
import NavBar from './components/NavBar'
import FinishedSheet from './components/FinishedSheet'

export default {
  name: 'App',
  components: {
        AbilityCalculator,
        NavBar,
        FinishedSheet
  },
  data () {
    return {
      characterName: '',
      pageChanger: 'home',
      finalClass: '',
      finalRace: '',
      attributesModifiers: {'Strength': 8 ,  'Dexterity': 8 , 'Constitution' : 8, 'Intelligence': 8 , 'Wisdom': 8, 'Charisma': 8},
      attributesTotalScores: {'Strength': 8 ,  'Dexterity': 8 , 'Constitution' : 8, 'Intelligence': 8 , 'Wisdom': 8, 'Charisma': 8},
      savingThrows: {},
      characterSavingThrowsBonuses: [],
      allClasses: dndClassesData || {},
      allRaces: dndRacesData || {},
    }
  },
  methods: {
    // getNewPageHome(newPage){
    //     this.pageChanger = newPage;
    // },
    getNewPageNavBar(newPage){
        this.pageChanger = newPage; 
    },
    getNewPageAbilityCalc(newPage){
        this.pageChanger = newPage;     
    },
    getNewMods(newMods){
        this.attributesModifiers = newMods; 
        this.getSavingThrows(this.attributesModifiers, this.characterSavingThrowsBonuses);
    },
    getNewTotal(newTotal){
        this.attributesTotalScores = newTotal;  
    },
    getNewCharName(newCharName){
        this.characterName = newCharName;  
    },
    getSavingThrowsBonuses(twoWords){
        this.characterSavingThrowsBonuses = twoWords.split(", ");
    },
    getSavingThrows(modifiers, bonuses){
        if(Object.keys(this.savingThrows).length !== 0){
            this.savingThrows = {};
        }
        for(let attribute in modifiers){
            for(let attributeWithBonus of bonuses){
                if(attribute === attributeWithBonus){
                    this.savingThrows[attribute] = modifiers[attribute] + 2;
                }
            }
            if(!this.savingThrows.hasOwnProperty(attribute)){
                this.savingThrows[attribute] = modifiers[attribute];
            }
        }
    },
    chooseClass(chosenClass){
      this.pageChanger = chosenClass;
    },
    chooseRace(chosenRace){
      this.pageChanger = chosenRace;
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
    finalChoiceOfClass(finalClassname){
       this.finalClass = finalClassname;
       this.getSavingThrowsBonuses(this.allClasses[this.finalClass].proficiencies.savingThrows);
       if(this.allRaces['Half-Elf'].halfElfExtraAttrs.length !== 0){
           this.allRaces['Half-Elf'].halfElfExtraAttrs = [];
       }
    },
    finalChoiceOfRace(finalRacename){
       this.finalRace = finalRacename;
       if(this.allRaces['Half-Elf'].halfElfExtraAttrs.length !== 0){
           this.allRaces['Half-Elf'].halfElfExtraAttrs = [];
       }
    },
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
  }
}
</script>

<style>
@import "../node_modules/bootstrap/dist/css/bootstrap.min.css";
@import './assets/main.css';
@import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Stencil+Display:wght@500&family=Fondamento&display=swap');
</style>