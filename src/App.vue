<template>
  <div id="app">
    <NavBar
        :navBarPageChanger="pageChanger"
        :navBarFinalClass="finalClass"
        :navBarFinalRace="finalRace"
        @changePage="getNewPage">
    </NavBar>
    <!-- <router-view></router-view> -->
    <template v-if="pageChanger === 'home'"> 
        <Home
          :homePageChanger="pageChanger"
          @changePage="getNewPage">
      </Home>
    </template>
    <template v-if="pageChanger === 'allClasses'">
      <AllClasses
          :allClassesPageChanger="pageChanger"
          :allClassesAllClasses="allClasses"
          @changePage="getNewPage">
      </AllClasses>
    </template>
    <template v-if="pageChanger === 'allRaces'">
      <AllRaces
          :allRacesPageChanger="pageChanger"
          :allRacesAllRaces="allRaces"
          @changePage="getNewPage">
      </AllRaces>
    </template>
    <div v-for="name in Object.keys(allClasses)" v-bind:key="name">
     <template v-if="pageChanger === name">
        <ClassPage
          :classPagePageChanger="pageChanger"
          :classPageFinalClass="finalClass"
          :classPageAllClasses="allClasses"
          @changePage="getNewPage"
          :classPageAllRaces="allRaces"
          @clearHalfElfAttrs="finalChoiceOfClass"
          @newFinalClass="finalChoiceOfClass">
        </ClassPage>
      </template>
    </div>
    <div v-for="name in Object.keys(allRaces)" v-bind:key="name">
      <template v-if="pageChanger === name">
        <RacePage
          :racePagePageChanger="pageChanger"
          :racePageFinalRace="finalRace"
          :racePageAllRaces="allRaces"
          @changePage="getNewPage"
          @clearHalfElfAttrs="finalChoiceOfRace"
          @newFinalRace="finalChoiceOfRace">
        </RacePage>
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
            @changePageAbilityCalc="getNewPage"
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
import RacePage from './components/RacePage'
import ClassPage from './components/ClassPage'
import AllRaces from './components/AllRaces'
import AllClasses from './components/AllClasses'
import Home from './components/Home'
// window.require = require('axios');
// import axios from 'axios';

export default {
  name: 'App',
  components: {
        AbilityCalculator,
        NavBar,
        FinishedSheet,
        RacePage,
        ClassPage,
        AllRaces,
        AllClasses,
        Home
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
  mounted() {
      let externalScript = document.createElement('script');
      externalScript.setAttribute('src', 'https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js');
      document.head.appendChild(externalScript);

      // // let externalScript2 = document.createElement('script');
      // // externalScript2.setAttribute('src', 'https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.16.0/umd/popper.min.j');
      // // document.head.appendChild(externalScript2);

        let externalScript3 = document.createElement('script');
        externalScript3.setAttribute('src', 'https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js');
        document.head.appendChild(externalScript3);
        console.log("ready");
  },
  methods: {
    getNewPage(newPage){
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
    // chooseClass(chosenClass){
    //   this.pageChanger = chosenClass;
    // },
    // chooseRace(chosenRace){
    //   this.pageChanger = chosenRace;
    // },
    finalChoiceOfClass(finalClassname){
       this.finalClass = finalClassname;
       this.getSavingThrowsBonuses(this.allClasses[this.finalClass].proficiencies.savingThrows);
       if(this.allRaces['Half-Elf'].halfElfExtraAttrs.length !== 0){
          this.allRaces['Half-Elf'].halfElfExtraAttrs = [];
       }
    },
    finalChoiceOfRace(finalRace, clearedArr){
       this.finalRace = finalRace;
       if(this.allRaces['Half-Elf'].halfElfExtraAttrs.length !== 0){
          this.allRaces['Half-Elf'].halfElfExtraAttrs = clearedArr;
       }
    },
  },
  // mounted: function() {
  //   axios.get('https://www.dnd5eapi.co/api/races')
  //     .then(response => this.allRaces = response.data);
  // }
}
</script>

<style>
@import "../node_modules/bootstrap/dist/css/bootstrap.min.css";
@import './assets/main.css';
@import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Stencil+Display:wght@500&family=Fondamento&display=swap');
</style>