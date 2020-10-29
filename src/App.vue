<template>
  	<div id="app">
    	<div class="row" v-if="pageChanger === 'home'"> 
      		<div class="col-6 front-page-class">
            <button v-on:click="pageChanger = 'allClasses'" type="button" class="btn btn-primary btn-lg front-page-class-button" >Class</button> 
      		</div>
      		<div class="col-6 front-page-race">
        		<button v-on:click="pageChanger = 'allRaces'" type="button" class="btn btn-primary btn-lg front-page-race-button" >Race</button>
      		</div>
    	</div>
      <div class="row" v-if="pageChanger === 'allClasses'">
            <div class="container all-classes">
                <div class="row all-classes-page-title">
                    <h1 class="dnd-classes-title">Classes</h1>
                </div>
                <div class="row all-classes-page-thumbnails">
                    <div v-for="dndClass in allClasses" :key="dndClass.name" class="figure col-3">
                        <img :src="dndClass.image" class="figure-img img-fluid rounded img-classes-thumbnails" alt="A generic square placeholder image with rounded corners in a figure.">
                        <!-- <div class="figure-caption">{{dndClass.introduction}}</div> -->
                        <button v-on:click="chooseClass(dndClass.name)" type="button" class="btn btn-primary" data-toggle="button" aria-pressed="false" autocomplete="off">{{dndClass.name}}</button>
                    </div>
                </div>
            </div>
        </div>
        <div class="row" v-if="pageChanger === 'Wizard'">
            <div class="col-10 classes-main-description">
              <div class="introduction-to-class">
                <h1 class="class-title-on-class-page">Wizard</h1>
                <p>Wizards are supreme magic-users, defined and united as a class by the spells they cast. Drawing on the subtle weave of magic that permeates the cosmos, wizards cast spells of explosive fire, arcing lightning, subtle deception, brute-force mind control, and much more.You must have an Intelligence score of 13 or higher in order to multiclass in or out of this class.</p>
              </div>
              <div class="row class-table">
                <table class="table">
                  <thead class="thead-dark header-of-class-table">
                    <tr>
                      <th scope="col">The Wizard</th>
                      <th scope="col" colspan=12 style="padding-left: 26%;">Spell Slots per Spell Level</th>
                    </tr>
                  </thead>
                  <thead class="thead-dark">
                    <tr>
                      <th scope="col">Level</th>
                      <th scope="col">Proficiency Bonus</th>
                      <th scope="col">Features</th>
                      <th scope="col">Cantrips Known</th>
                      <th scope="col">1st</th>
                      <th scope="col">2nd</th>
                      <th scope="col">3rd</th>
                      <th scope="col">4th</th>
                      <th scope="col">5th</th>
                      <th scope="col">6th</th>
                      <th scope="col">7th</th>
                      <th scope="col">8th</th>
                      <th scope="col">9th</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr>
                      <th scope="row">1</th>
                      <td>+2</td>
                      <td>Spellcasting, Arcane Recovery</td>
                      <td>3</td>
                      <td>2</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">2</th>
                      <td>+2</td>
                      <td>Arcane Tradition</td>
                      <td>3</td>
                      <td>3</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">3</th>
                      <td>+2</td>
                      <td></td>
                      <td>3</td>
                      <td>4</td>
                      <td>2</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                       <tr>
                      <th scope="row">4</th>
                      <td>+2</td>
                      <td>Ability Score Improvement</td>
                      <td>4</td>
                      <td>4</td>
                      <td>3</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">5</th>
                      <td>+3</td>
                      <td>Arcane Tradition</td>
                      <td>4</td>
                      <td>4</td>
                      <td>3</td>
                      <td>2</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                    <tr>
                    <th scope="row">6</th>
                      <td>+3</td>
                      <td>Arcane Tradition feature</td>
                      <td>4</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">7</th>
                      <td>+3</td>
                      <td></td>
                      <td>4</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>1</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">8</th>
                      <td>+3</td>
                      <td>Ability Score Improvement</td>
                      <td>4</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>2</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">9</th>
                      <td>+4</td>
                      <td></td>
                      <td>4</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>1</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">10</th>
                      <td>+4</td>
                      <td>Arcane Tradition feature</td>
                      <td>5</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>2</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">11</th>
                      <td>+4</td>
                      <td></td>
                      <td>5</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>2</td>
                      <td>1</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                       <tr>
                      <th scope="row">12</th>
                      <td>+4</td>
                      <td>Ability Score Improvement</td>
                      <td>5</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>2</td>
                      <td>1</td>
                      <td>-</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">13</th>
                      <td>+5</td>
                      <td></td>
                      <td>5</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>2</td>
                      <td>1</td>
                      <td>1</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">14</th>
                      <td>+5</td>
                      <td>Arcane Tradition feature</td>
                      <td>5</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>2</td>
                      <td>1</td>
                      <td>1</td>
                      <td>-</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">15</th>
                      <td>+5</td>
                      <td></td>
                      <td>5</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>2</td>
                      <td>1</td>
                      <td>1</td>
                      <td>1</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">16</th>
                      <td>+5</td>
                      <td>Ability Score Improvement</td>
                      <td>5</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>2</td>
                      <td>1</td>
                      <td>1</td>
                      <td>1</td>
                      <td>-</td>
                    </tr>
                    <tr>
                      <th scope="row">17</th>
                      <td>+6</td>
                      <td></td>
                      <td>5</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>2</td>
                      <td>1</td>
                      <td>1</td>
                      <td>1</td>
                      <td>1</td>
                    </tr>
                    <tr>
                      <th scope="row">18</th>
                      <td>+6</td>
                      <td>Spell Mastery</td>
                      <td>5</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>1</td>
                      <td>1</td>
                      <td>1</td>
                      <td>1</td>
                    </tr>
                    <tr>
                      <th scope="row">19</th>
                      <td>+6</td>
                      <td>Signature Spells</td>
                      <td>5</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>2</td>
                      <td>1</td>
                      <td>1</td>
                      <td>1</td>
                    </tr>
                    <tr>
                      <th scope="row">20</th>
                      <td>+6</td>
                      <td>Arcane Tradition</td>
                      <td>5</td>
                      <td>4</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>3</td>
                      <td>2</td>
                      <td>2</td>
                      <td>1</td>
                      <td>1</td>
                    </tr>
                  </tbody>
                </table>
              </div>
              <div class="class-detailed-description">
                <h1>Class Features</h1>
                <h5>Hit Points</h5>
                  <p>
                    <strong>Hit Dice:</strong>
                    1d6 per wizard level
                    <br>
                    <strong>Hit Points at 1st Level:</strong>
                    6 + your Constitution modifier
                    <br>
                    <strong>Hit Points at Higher Levels:</strong>
                    1d6 (or 4) + your Constitution modifier per wizard level after 1st
                    <br>
                  </p>
              </div>
            </div>
            <div class="col-2 classes-sidebar-recommendations">
                <h2>Similar Classes</h2>
                <h3>Sorcerer</h3>
                <h4>Similarities: Spellcasters, No Armor, Small Hit Die, Huge Variety Of Spells</h4>
                <button v-on:click="chooseClass('Sorcerer')" type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">Sorcerer</button>
                <h3>Bard</h3>
                <h4>Similarities: Spellcasters, Huge Variety Of Spells</h4>
                <button v-on:click="chooseClass('Bard')" type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">Bard</button>
                <h2>Suitable Races</h2>
                <h3>Gnome</h3>
                <h4>Race Bonuses: +2 Intelligence</h4>
                <button type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">Gnome</button>
                <h3>Vedalken</h3>
                <h4>Race Bonuses: +2 Intelligence</h4>
                <button type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">Vedalken</button>
            </div>
        </div>
      </div> 
</template>

<script>
// import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  // components: {
  //   HelloWorld
  // },
  data () {
    return {
      pageChanger: 'home',
      allClasses: [
        {
          name: 'Fighter',
          image: "https://i.pinimg.com/564x/4b/bf/a1/4bbfa114bbb19afeaf740b7d45f67aee.jpg",
          introduction: 'swings sword',
          hitPoints: {
            hitDice: '1d10 per fighter level',
            hitPointsAtFirstLevel: '10 + your Constitution modifier',
            hitPointsAtHigherLevels: '1d10 (or 6) + your Constitution modifier per fighter level after 1st'
          },
          proficiencies: {
          armor: 'All armor, shields',
          weapons: 'Simple weapons, martial weapons',
          tools: 'None',
          savingThrows: 'Strength, Constitution',
          skills: 'Choose two skills from Acrobatics, Animal Handling, Athletics, History, Insight, Intimidation, Perception, and Survival',
          }
        },
        {
          name: 'Wizard',
          image: "https://i.pinimg.com/564x/ac/36/54/ac36540927acd0021025724e83ca028d.jpg",
          introduction: 'throws fireballs',
          hitPoints: {
            hitDice: '1d6 per wizard level',
            hitPointsAtFirstLevel: '6 + your Constitution modifier',
            hitPointsAtHigherLevels: '1d6 (or 4) + your Constitution modifier per wizard level after 1st'
          },
          proficiencies: {
          armor: 'None',
          weapons: 'Daggers, darts, slings, quarterstaffs, light crossbows',
          tools: 'None',
          savingThrows: 'Intelligence, Wisdom',
          skills: 'Choose two from Arcana, History, Insight, Investigation, Medicine, and Religion',
          }
        },
        {
          name: 'Rogue',
          image: "https://i.pinimg.com/564x/01/56/c7/0156c7576b1704ee70a55e4d1bd0db74.jpg",
          introduction: 'stabs people from stealth',
          hitPoints: {
            hitDice: '1d8 per rogue level',
            hitPointsAtFirstLevel: '8 + your Constitution modifier',
            hitPointsAtHigherLevels: '1d8 (or 5) + your Constitution modifier per rogue level after 1st'
          },
          proficiencies: {
          armor: 'Light armor',
          weapons: 'Simple weapons, hand crossbows, longswords, rapiers, shortswords',
          tools: 'Thieves\' tools',
          savingThrows: 'Dexterity, Intelligence',
          skills: 'Choose four from Acrobatics, Athletics, Deception, Insight, Intimidation, Investigation, Perception, Performance, Persuasion, Sleight of Hand, and Stealth',
          }
        },
        {
          name: 'Cleric',
          image: "https://i.pinimg.com/236x/aa/35/f7/aa35f7c05afbc9e47fa73a9922a9c4ce.jpg",
          introduction: 'blesses people and kills undead',
          hitPoints: {
            hitDice: '1d8 per cleric level',
            hitPointsAtFirstLevel: '8 + your Constitution modifier',
            hitPointsAtHigherLevels: '1d8 (or 5) + your Constitution modifier per cleric level after 1st'
          },
          proficiencies: {
          armor: 'Light armor, medium armor, shields',
          weapons: 'All simple weapons',
          tools: 'None',
          savingThrows: 'Wisdom, Charisma',
          skills: 'Choose two from History, Insight, Medicine, Persuasion, and Religion',
          }
        },
        {
          name: 'Druid',
          image: "https://i.pinimg.com/564x/22/15/e0/2215e0b60512e6055cbbee026a2d3f03.jpg",
          introduction: 'most likely vegan or trying to get into it',
          hitPoints: {
            hitDice: '1d8 per druid level',
            hitPointsAtFirstLevel: '8 + your Constitution modifier',
            hitPointsAtHigherLevels: '1d8 (or 5) + your Constitution modifier per druid level after 1st'
          },
          proficiencies: {
          armor: 'Light armor, medium armor, shields (druids will not wear armor or use shields made of metal)',
          weapons: 'Clubs, daggers, darts, javelins, maces, quarterstaffs, scimitars, sickles, slings, spears',
          tools: 'Herbalism kit',
          savingThrows: 'Intelligence, Wisdom',
          skills: 'Choose two from Arcana, Animal Handling, Insight, Medicine, Nature, Perception, Religion, and Survival',
          }
        },
        {
          name: 'Monk',
          image: "https://i.pinimg.com/564x/a5/ce/6a/a5ce6a1c7e6479c6e2f670e4e89c06e3.jpg",
          introduction: 'Though the river tells no lies, the dishonest standing on the shore, still hear them',
          hitPoints: {
            hitDice: '1d8 per monk level',
            hitPointsAtFirstLevel: '8 + your Constitution modifier',
            hitPointsAtHigherLevels: '1d8 (or 5) + your Constitution modifier per monk level after 1st'
          },
          proficiencies: {
          armor: 'None',
          weapons: 'Simple weapons, shortswords',
          tools: 'Choose one type of artisan\'s tools or one musical instrument',
          savingThrows: 'Strength, Dexterity',
          skills: 'Choose two from Acrobatics, Athletics, History, Insight, Religion, and Stealth',
          }
        },
        {
          name: 'Paladin',
          image: "https://i.pinimg.com/564x/3f/7a/1d/3f7a1d4c8789ac516f6ca0d2dfcd535a.jpg",
          introduction: 'smites things with religious vigor',
          hitPoints: {
            hitDice: '1d10 per paladin level',
            hitPointsAtFirstLevel: '10 + your Constitution modifier',
            hitPointsAtHigherLevels: '1d10 (or 6) + your Constitution modifier per paladin level after 1st'
          },
          proficiencies: {
          armor: 'All armor, shields',
          weapons: 'Simple weapons, martial weapons',
          tools: 'None',
          savingThrows: 'Wisdom, Charisma',
          skills: 'Choose two from Athletics, Insight, Intimidation, Medicine, Persuasion, and Religion',
          }
        },
        {
          name: 'Ranger',
          image: "https://i.pinimg.com/564x/bf/de/2e/bfde2e3129b297513595c0dc9aea16d2.jpg",
          introduction: 'single, loves hiking and animals',
          hitPoints: {
            hitDice: '1d10 per ranger level',
            hitPointsAtFirstLevel: '10 + your Constitution modifier',
            hitPointsAtHigherLevels: '1d10 (or 6) + your Constitution modifier per ranger level after 1st'
          },
          proficiencies: {
          armor: 'Light armor, medium armor, shields',
          weapons: 'Simple weapons, martial weapons',
          tools: 'None',
          savingThrows: 'Strength, Dexterity',
          skills: 'Choose three from Animal Handling, Athletics, Insight, Investigation, Nature, Perception, Stealth, and Survival',
          }
        },
        {
          name: 'Sorcerer',
          image: "https://i.pinimg.com/564x/12/ab/e6/12abe68c7cda152e2a81f9e500c68a02.jpg",
          introduction: 'just born that way',
          hitPoints: {
            hitDice: '1d6 per sorcerer level',
            hitPointsAtFirstLevel: '6 + your Constitution modifier',
            hitPointsAtHigherLevels: '1d6 (or 4) + your Constitution modifier per sorcerer level after 1st'
          },
          proficiencies: {
          armor: 'None',
          weapons: 'Daggers, darts, slings, quarterstaffs, light crossbows',
          tools: 'None',
          savingThrows: 'Constitution, Charisma',
          skills: 'Choose two from Arcana, Deception, Insight, Intimidation, Persuasion, and Religion',
          }
        },
        {
          name: 'Warlock',
          image: "https://i.pinimg.com/564x/95/e9/9d/95e99d65e126b63e3daf5b590ca23b00.jpg",
          introduction: 'very dark and edgy',
          hitPoints: {
            hitDice: '1d8 per warlock level',
            hitPointsAtFirstLevel: '8 + your Constitution modifier',
            hitPointsAtHigherLevels: '1d8 (or 5) + your Constitution modifier per warlock level after 1st'
          },
          proficiencies: {
          armor: 'Light armor',
          weapons: 'Simple weapons',
          tools: 'None',
          savingThrows: 'Wisdom, Charisma',
          skills: 'Choose two from Arcana, Deception, History, Intimidation, Investigation, Nature, and Religion',
          }
        },
        {
          name: 'Bard',
          image: "https://i.pinimg.com/564x/ff/0b/90/ff0b907eec84bb483ad612093514dc56.jpg",
          introduction: 'influencer',
          hitPoints: {
            hitDice: '1d8 per bard level',
            hitPointsAtFirstLevel: '8 + your Constitution modifier',
            hitPointsAtHigherLevels: '1d8 (or 5) + your Constitution modifier per bard level after 1st'
          },
          proficiencies: {
          armor: 'Light armor',
          weapons: 'Simple weapons, hand crossbows, longswords, rapiers, shortswords',
          tools: 'Three musical instruments of your choice',
          savingThrows: 'Dexterity, Charisma',
          skills: 'Choose any three',
          }
        },
        {
          name: 'Barbarian',
          image: "https://i.pinimg.com/564x/4a/a0/b7/4aa0b7c762d03855391f8c40ab140b6e.jpg",
          introduction: 'self-explanatory',
          hitPoints: {
            hitDice: '1d12 per barbarian level',
            hitPointsAtFirstLevel: '12 + your Constitution modifier',
            hitPointsAtHigherLevels: '1d12 (or 7) + your Constitution modifier per barbarian level after 1st'
          },
          proficiencies: {
          armor: 'Light armor, medium armor, shields',
          weapons: 'Simple weapons, martial weapons',
          tools: 'None',
          savingThrows: 'Strength, Constitution',
          skills: 'Choose two from Animal Handling, Athletics, Intimidation, Nature, Perception, and Survival',
          }
        },
      ]
    }
  },
  // watch: {
  //   pageChanger: function (val) {
  //     console.log(this.pageChanger);
  //   }
  // },
  methods: {
    chooseClass(chosenClass){
      this.pageChanger = chosenClass;
    }
  }
}
</script>

<style>
@import "../node_modules/bootstrap/dist/css/bootstrap.min.css";
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
  height: 100%;
  background-color: #3f473a;
}
html, body, .row, .col-6 {
  height: 100%;
}
.front-page-class{
  height: 100%;
  background-color:  #3e3731;
}
.front-page-race{
  height: 100%;
  background-color: #3f473a;
}
.front-page-class-button{
  padding-top: 8px;
  margin-top: 45%;
}
.front-page-race-button{
  padding-top: 8px;
  margin-top: 45%;
}
.all-classes-page-title{
  height: 5%;
  padding-left: 50%;
}
.img-classes-thumbnails{
  height: 400px;
  width: 250px;
}
.figure-caption{
  width: 50%;
  margin-left: 25%;
  color: #000;
  font-size: 17px;
}
.dnd-classes-title{
  margin-left: -9%;
  color: #151515;
}
.all-classes{
  background-color: #3e3731;
}
.btn-primary{
  color: #cecece;
  background-color: #462025;
  border-color: #462025;
}
.btn-primary:hover, .btn-primary:active{
  background-color: #2b1417;
  border-color:  #2b1417; 
}
html{
  background-color: #3f473a;
}
h2,h3,h4{
  color: #000;
  padding: 5px;
}
.classes-sidebar-recommendations{
  background-color: #3e3731;
}
.recommendations{
  padding: 5px;
}
.recommendations:hover, .recommendations:active{
  background-color: #2b1417;
  border-color:  #2b1417; 
}
p{
  color: #000;
}
.class-title-on-class-page{
   color: #151515;
}
</style>
