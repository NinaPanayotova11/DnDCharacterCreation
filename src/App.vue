<template>
  <div id="app">
    <template v-if="pageChanger === 'home'"> 
      <div class= "row">
        <div class="col-12">
          <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <a class="navbar-brand" href="#">Navbar</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavDropdown" aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
              <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNavDropdown">
              <ul class="navbar-nav">
                <li class="nav-item active">
                  <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
                </li>
                <li class="nav-item dropdown">
                  <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                    Dropdown link
                  </a>
                  <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
                    <a class="dropdown-item" href="#">Action</a>
                    <a class="dropdown-item" href="#">Another action</a>
                    <a class="dropdown-item" href="#">Something else here</a>
                  </div>
                </li>
              </ul>
            </div>
          </nav>
        </div>
      </div>
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
          <div class="col-12">
          <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <a class="navbar-brand" href="#">Navbar</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavDropdown" aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
              <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNavDropdown">
              <ul class="navbar-nav">
                <li class="nav-item active">
                  <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
                </li>
                <li class="nav-item dropdown">
                  <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                    Dropdown link
                  </a>
                  <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
                    <a class="dropdown-item" href="#">Action</a>
                    <a class="dropdown-item" href="#">Another action</a>
                    <a class="dropdown-item" href="#">Something else here</a>
                  </div>
                </li>
              </ul>
            </div>
          </nav>
        </div>
        </div>
        <div class="row">
          <div class= 'container classes-container'>
            <div class="col-12">
              <div class="row all-classes-page-title">
                  <h1 class="dnd-classes-title">Classes</h1>
              </div>
              <div class="row all-classes-page-thumbnails">
                  <div v-for="dndClass in allClasses" :key="dndClass.name" class="figure col-3">
                      <img :src="dndClass.image" class="figure-img img-fluid rounded img-classes-thumbnails" alt="A generic square placeholder image with rounded corners in a figure.">
                      <button v-on:click="chooseClass(dndClass.name)" type="button" class="btn btn-primary" data-toggle="button" aria-pressed="false" autocomplete="off">{{dndClass.name}}</button>
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
          <div class="col-12">
          <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <a class="navbar-brand" href="#">Navbar</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavDropdown" aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
              <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNavDropdown">
              <ul class="navbar-nav">
                <li class="nav-item active">
                  <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
                </li>
                <li class="nav-item dropdown">
                  <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                    Dropdown link
                  </a>
                  <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
                    <a class="dropdown-item" href="#">Action</a>
                    <a class="dropdown-item" href="#">Another action</a>
                    <a class="dropdown-item" href="#">Something else here</a>
                  </div>
                </li>
              </ul>
            </div>
          </nav>
        </div>
        </div>
        <div class="row">
          <div class="container races-container">
            <div class="col-12">
              <div class="row all-races-page-title">
                <h1 class="dnd-races-title">Races</h1>
              </div>
              <div class="row all-races-page-thumbnails">
                <div v-for="dndRace in allRaces" :key="dndRace.name" class="figure col-3">
                    <img :src="dndRace.image" class="figure-img img-fluid rounded img-classes-thumbnails" alt="A generic square placeholder image with rounded corners in a figure.">
                    <button v-on:click="chooseRace(dndRace.name)" type="button" class="btn btn-primary" data-toggle="button" aria-pressed="false" autocomplete="off">{{dndRace.name}}</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </template>
    <template v-if="pageChanger === 'Wizard' || pageChanger === 'Cleric' || pageChanger === 'Druid' || pageChanger === 'Fighter' || pageChanger === 'Rogue' || pageChanger === 'Barbarian' || pageChanger === 'Warlock' || pageChanger === 'Ranger' || pageChanger === 'Paladin' || pageChanger === 'Monk' || pageChanger === 'Sorcerer' || pageChanger === 'Bard'">
      <div class="class-page">
        <div class="row">
          <div class="col-12">
            <nav class="navbar navbar-expand-lg navbar-light bg-light">
              <a class="navbar-brand" href="#">Navbar</a>
              <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavDropdown" aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
              </button>
              <div class="collapse navbar-collapse" id="navbarNavDropdown">
                <ul class="navbar-nav">
                  <li class="nav-item active">
                    <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
                  </li>
                  <li class="nav-item dropdown">
                    <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                      Dropdown link
                    </a>
                    <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
                      <a class="dropdown-item" href="#">Action</a>
                      <a class="dropdown-item" href="#">Another action</a>
                      <a class="dropdown-item" href="#">Something else here</a>
                    </div>
                  </li>
                </ul>
              </div>
            </nav>
          </div>
        </div>
        <div class="row">
            <div class="container class-page">
              <div class="row">
                <div class="col-9 classes-main-description">
                  <div class="introduction-to-class">
                    <h1 class="class-title-on-class-page">{{allClasses[pageChanger].name}}</h1>
                    <p class="class-mini-description-on-class-page">{{allClasses[pageChanger].introduction}}</p>
                  </div>
                  <div class="row class-table">
                    <table class="table dnd-class-table">
                      <thead class="thead-dark header-of-class-table">
                        <tr>
                          <th scope="col" colspan=2 style='text-align: start'>The {{allClasses[pageChanger].name}}</th>
                          <th v-if="allClasses[pageChanger].type == 'Spellcaster' || allClasses[pageChanger].type == 'halfSpellcaster'" scope="col" colspan=11 style="padding-left: 3%;">Spell Slots per Spell Level</th>
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
    <template v-if="pageChanger === 'Human' || pageChanger === 'Elf' || pageChanger === 'Halfling' || pageChanger === 'Half-Orc' || pageChanger === 'Half-Elf' || pageChanger === 'Tiefling' || pageChanger === 'Dwarf' || pageChanger === 'Dragonborn' || pageChanger === 'Gnome'">
      <div class="race-page">
        <div class="row">
          <div class="col-12">
          <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <a class="navbar-brand" href="#">Navbar</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavDropdown" aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
              <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNavDropdown">
              <ul class="navbar-nav">
                <li class="nav-item active">
                  <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
                </li>
                <li class="nav-item dropdown">
                  <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                    Dropdown link
                  </a>
                  <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
                    <a class="dropdown-item" href="#">Action</a>
                    <a class="dropdown-item" href="#">Another action</a>
                    <a class="dropdown-item" href="#">Something else here</a>
                  </div>
                </li>
              </ul>
            </div>
          </nav>
        </div>
        </div>
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
                  <button v-on:click="finalChoiceOfRace(allRaces[pageChanger].name)" type="button" class="btn btn-primary btn-lg recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">
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
      finalClass: '',
      finalRace: '',
      allClasses: {
        'Fighter':{
          name: 'Fighter',
          type: 'nonSpellcaster',
          image: "https://i.pinimg.com/564x/4b/bf/a1/4bbfa114bbb19afeaf740b7d45f67aee.jpg",
          introduction: 'Fighters share an unparalleled mastery with weapons and armor, and a thorough knowledge of the skills of combat. They are well acquainted with death, both meting it out and staring it defiantly in the face. You must have a Dexterity or Strength score of 13 or higher in order to multiclass in or out of this class.',
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
          },
          levels: {
            1: {
              proficiencyBonus: '+2',
              feature: "Fighting Style, Second Wind",
            },
            2: {
              proficiencyBonus: '+2',
              feature: "Action Surge (x1)",
            },
            3: {
              proficiencyBonus: '+2',
              feature: 'Martial Archetype',
            },
            4: {
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
            },
            5: {
              proficiencyBonus: '+3',
              feature: "Extra Attack (x1)",
            },
            6: {
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
            },
            7: {
              proficiencyBonus: '+3',
              feature: 'Martial Archetype feature',
            },
            8: {
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
            },
            9: {
              proficiencyBonus: '+4',
              feature: 'Indomitable (x1)',
            },
            10: {
              proficiencyBonus: '+4',
              feature: "Martial Archetype feature",
            },
            11: {
              proficiencyBonus: '+4',
              feature: "Extra Attack (x2)", 
            },
            12: {
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
            },
            13: {
              proficiencyBonus: '+5',
              feature: 'Indomitable (x2)',
            },
            14: {
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
            },
            15: {
              proficiencyBonus: '+5',
              feature: 'Martial Archetype feature',
            },
            16: {
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
            },
            17: {
              proficiencyBonus: '+6',
              feature: "Action Surge (x2), Indomitable (x3)",
            },
            18: {
              proficiencyBonus: '+6',
              feature: "Martial Archetype feature",
            },
            19: {
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
            },
            20: {
              proficiencyBonus: '+6',
              feature: "Extra Attack (x3)",
            }
          },
          similarClasses: {
            firstName: 'Barbarian',
            firstDescription: ' Both Require Strength, Similar Aesthetic',
            secondName: 'Paladin',
            secondDescription: ' Similar Proficiencies, Fighting Style, Both Require Strength',
          },
          suitableRaces: {
            firstName: 'Half-Orc',
            firstDescription: ' +2 Strength',
            secondName: 'Dragonborn',
            secondDescription: ' +2 Strength',
          },
        },
        'Wizard':{
          name: 'Wizard',
          type: 'Spellcaster',
          image: "https://i.pinimg.com/564x/ac/36/54/ac36540927acd0021025724e83ca028d.jpg",
          introduction: 'Wizards are supreme magic-users, defined and united as a class by the spells they cast. Drawing on the subtle weave of magic that permeates the cosmos, wizards cast spells of explosive fire, arcing lightning, subtle deception, brute-force mind control, and much more.You must have an Intelligence score of 13 or higher in order to multiclass in or out of this class.',
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
          },
          levels: {
            1: {
              proficiencyBonus: '+2',
              feature: "Spellcasting, Arcane Recovery",
              cantrips: 3,
              spellSlots: [2, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            2: {
              proficiencyBonus: '+2',
              feature: "Arcane Tradition",
              cantrips: 3,
              spellSlots: [3, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            3: {
              proficiencyBonus: '+2',
              feature: '',
              cantrips: 3,
              spellSlots: [4, 2, '-', '-', '-', '-', '-', '-', '-']
            },
            4: {
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [4, 3, '-', '-', '-', '-', '-', '-', '-']
            },
            5: {
              proficiencyBonus: '+3',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 2, '-', '-', '-', '-', '-', '-']
            },
            6: {
              proficiencyBonus: '+3',
              feature: "Arcane Tradition feature", 
              cantrips: 4,
              spellSlots: [4, 3, 3, '-', '-', '-', '-', '-', '-']
            },
            7: {
              proficiencyBonus: '+3',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 1, '-', '-', '-', '-', '-']
            },
            8: {
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [4, 3, 3, 2, '-', '-', '-', '-', '-']
            },
            9: {
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 1, '-', '-', '-', '-']
            },
            10: {
              proficiencyBonus: '+4',
              feature: "Arcane Tradition feature",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, '-', '-', '-', '-']
            },
            11: {
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            12: {
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            13: {
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            14: {
              proficiencyBonus: '+5',
              feature: 'Arcane Tradition feature',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            15: {
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            16: {
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement", 
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            17: {
              proficiencyBonus: '+6',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, 1]
            },
            18: {
              proficiencyBonus: '+6',
              feature: "Spell Mastery",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 3, 1, 1, 1, 1]
            },
            19: {
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 3, 2, 1, 1, 1]
            },
            20: {
              proficiencyBonus: '+6',
              feature: "Signature Spells",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 3, 2, 2, 1, 1]
            }
          },
          similarClasses: {
            firstName: 'Sorcerer',
            firstDescription: ' Spellcasters, No Armor, Small Hit Die, Huge Variety Of Spells',
            secondName: 'Bard',
            secondDescription: ' Spellcasters, Huge Variety Of Spells, Both Require Charisma',
          },
          suitableRaces: {
            firstName: 'Gnome',
            firstDescription: ' +2 Intelligence',
            secondName: 'Tiefling',
            secondDescription: ' +1 Intelligence',
          },
        },
        'Rogue':{
          name: 'Rogue',
          type: 'nonSpellcaster',
          image: "https://i.pinimg.com/564x/01/56/c7/0156c7576b1704ee70a55e4d1bd0db74.jpg",
          introduction: 'Rogues rely on skill, stealth, and their foes\' vulnerabilities to get the upper hand in any situation. They have a knack for finding the solution to just about any problem, demonstrating a resourcefulness and versatility that is the cornerstone of any successful adventuring party.You must have a Dexterity score of 13 or higher in order to multiclass in or out of this class.',
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
          },
          levels: {
            1: {
              proficiencyBonus: '+2',
              sneakAttack: '1d6',
              feature: "Expertise, Sneak Attack, Thieves' Cant",
            },
            2: {
              proficiencyBonus: '+2',
              sneakAttack: '1d6',
              feature: "Cunning Action",
            },
            3: {
              proficiencyBonus: '+2',
              sneakAttack: '2d6',
              feature: 'Roguish Archetype',
            },
            4: {
              proficiencyBonus: '+2',
              sneakAttack: '2d6',
              feature: "Ability Score Improvement",
            },
            5: {
              proficiencyBonus: '+3',
              sneakAttack: '3d6',
              feature: "Uncanny Dodge",
            },
            6: {
              proficiencyBonus: '+3',
              sneakAttack: '3d6',
              feature: "Expertise",
            },
            7: {
              proficiencyBonus: '+3',
              sneakAttack: '4d6',
              feature: 'Evasion',
            },
            8: {
              proficiencyBonus: '+3',
              sneakAttack: '4d6',
              feature: "Ability Score Improvement",
            },
            9: {
              proficiencyBonus: '+4',
              sneakAttack: '5d6',
              feature: 'Roguish Archetype feature',
            },
            10: {
              proficiencyBonus: '+4',
              sneakAttack: '5d6',
              feature: "Ability Score Improvement",
            },
            11: {
              proficiencyBonus: '+4',
              sneakAttack: '6d6',
              feature: "Reliable Talent", 
            },
            12: {
              proficiencyBonus: '+4',
              sneakAttack: '6d6',
              feature: "Ability Score Improvement",
            },
            13: {
              proficiencyBonus: '+5',
              sneakAttack: '7d6',
              feature: 'Roguish Archetype feature',
            },
            14: {
              proficiencyBonus: '+5',
              sneakAttack: '7d6',
              feature: "Blindsense",
            },
            15: {
              proficiencyBonus: '+5',
              sneakAttack: '8d6',
              feature: 'Slippery Mind',
            },
            16: {
              proficiencyBonus: '+5',
              sneakAttack: '8d6',
              feature: "Ability Score Improvement",
            },
            17: {
              proficiencyBonus: '+6',
              sneakAttack: '9d6',
              feature: "Roguish Archetype feature",
            },
            18: {
              proficiencyBonus: '+6',
              sneakAttack: '9d6',
              feature: "Elusive",
            },
            19: {
              proficiencyBonus: '+6',
              sneakAttack: '10d6',
              feature: "Ability Score Improvement",
            },
            20: {
              proficiencyBonus: '+6',
              sneakAttack: '10d6',
              feature: "Stroke of Luck",
            }
          },
          similarClasses: {
            firstName: 'Ranger',
            firstDescription: ' Both Require Dexterity, Both Can be Stealthy',
            secondName: 'Bard',
            secondDescription: ' Both Have Expertise, Similar Style',
          },
          suitableRaces: {
            firstName: 'Halfling',
            firstDescription: ' +2 Dexterity',
            secondName: 'Elf',
            secondDescription: ' +2 Dexterity',
          },
        },
        'Cleric':{
          name: 'Cleric',
          type: 'Spellcaster',
          image: "https://i.pinimg.com/236x/aa/35/f7/aa35f7c05afbc9e47fa73a9922a9c4ce.jpg",
          introduction: 'Clerics are intermediaries between the mortal world and the distant planes of the gods. As varied as the gods they serve, clerics strive to embody the handiwork of their deities. No ordinary priest, a cleric is imbued with divine magic. You must have a Wisdom score of 13 or higher in order to multiclass in or out of this class.',
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
          },
          levels: {
            1: {
              proficiencyBonus: '+2',
              feature: "Spellcasting, Divine Domain",
              cantrips: 3,
              spellSlots: [2, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            2: {
              proficiencyBonus: '+2',
              feature: "Channel Divinity (x1), Divine Domain feature",
              cantrips: 3,
              spellSlots: [3, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            3: {
              proficiencyBonus: '+2',
              feature: '',
              cantrips: 3,
              spellSlots: [4, 2, '-', '-', '-', '-', '-', '-', '-']
            },
            4: {
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [4, 3, '-', '-', '-', '-', '-', '-', '-']
            },
            5: {
              proficiencyBonus: '+3',
              feature: "Destroy Undead (CR 1/2)",
              cantrips: 4,
              spellSlots: [4, 3, 2, '-', '-', '-', '-', '-', '-']
            },
            6: {
              proficiencyBonus: '+3',
              feature: "Channel Divinity (x2), Divine Domain feature",
              cantrips: 4,
              spellSlots: [4, 3, 3, '-', '-', '-', '-', '-', '-']
            },
            7: {
              proficiencyBonus: '+3',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 1, '-', '-', '-', '-', '-']
            },
            8: {
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement, Destroy Undead (CR 1), Divine Domain feature",
              cantrips: 4,
              spellSlots: [4, 3, 3, 2, '-', '-', '-', '-', '-']
            },
            9: {
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 1, '-', '-', '-', '-']
            },
            10: {
              proficiencyBonus: '+4',
              feature: "Divine Intervention",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, '-', '-', '-', '-']
            },
            11: {
              proficiencyBonus: '+4',
              feature: "Destroy Undead (CR 2)", 
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            12: {
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            13: {
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            14: {
              proficiencyBonus: '+5',
              feature: "Destroy Undead (CR 3)",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            15: {
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            16: {
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            17: {
              proficiencyBonus: '+6',
              feature: "Destroy Undead (CR 4), Divine Domain feature",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, 1]
            },
            18: {
              proficiencyBonus: '+6',
              feature: "Channel Divinity (x3)",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 3, 1, 1, 1, 1]
            },
            19: {
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 3, 2, 1, 1, 1]
            },
            20: {
              proficiencyBonus: '+6',
              feature: "Divine Intervention improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 3, 2, 2, 1, 1]
            }
          },
          similarClasses: {
            firstName: 'Druid',
            firstDescription: ' Spellcasters, Average Hit Die, Huge Variety Of Healing Spells',
            secondName: 'Paladin',
            secondDescription: ' Similar Lore, Ability to Cast Spells',
          },
          suitableRaces: {
            firstName: 'Human',
            firstDescription: ' +1 to All Ability Scores',
            secondName: 'Half-Elf',
            secondDescription: ' +1 to Two Ability Scores, +2 to Charisma',
          },
        },
        'Druid':{
          name: 'Druid',
          type: 'Spellcaster',
          image: "https://i.pinimg.com/564x/22/15/e0/2215e0b60512e6055cbbee026a2d3f03.jpg",
          introduction: 'Whether calling on the elemental forces of nature or emulating the creatures of the animal world, druids are an embodiment of nature\'s resilience, cunning, and fury. They claim no mastery over nature, but see themselves as extensions of nature\'s indomitable will. You must have a Wisdom score of 13 or higher in order to multiclass in or out of this class.',
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
          },
          levels: {
            1: {
              proficiencyBonus: '+2',
              feature: "Druidic, Spellcasting", 
              cantrips: 2,
              spellSlots: [2, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            2: {
              proficiencyBonus: '+2',
              feature: "Wild Shape, Druid Circle", 
              cantrips: 2,
              spellSlots: [3, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            3: {
              proficiencyBonus: '+2',
              feature: '',
              cantrips: 2,
              spellSlots: [4, 2, '-', '-', '-', '-', '-', '-', '-']
            },
            4: {
              proficiencyBonus: '+2',
              feature: "Wild Shape improvement, Ability Score Improvement", 
              cantrips: 3,
              spellSlots: [4, 3, '-', '-', '-', '-', '-', '-', '-']
            },
            5: {
              proficiencyBonus: '+3',
              feature: '',
              cantrips: 3,
              spellSlots: [4, 3, 2, '-', '-', '-', '-', '-', '-']
            },
            6: {
              proficiencyBonus: '+3',              
              feature: "Druid Circle feature", 
              cantrips: 3,
              spellSlots: [4, 3, 3, '-', '-', '-', '-', '-', '-']
            },
            7: {
              proficiencyBonus: '+3',
              feature: '',
              cantrips: 3,
              spellSlots: [4, 3, 3, 1, '-', '-', '-', '-', '-']
            },
            8: {
              proficiencyBonus: '+3',
              feature: "Wild Shape improvement, Ability Score Improvement", 
              cantrips: 3,
              spellSlots: [4, 3, 3, 2, '-', '-', '-', '-', '-']
            },
            9: {
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 3,
              spellSlots: [4, 3, 3, 3, 1, '-', '-', '-', '-']
            },
            10: {
              proficiencyBonus: '+4',
              feature: "Druid Circle feature", 
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, '-', '-', '-', '-']
            },
            11: {
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            12: {
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            13: {
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            14: {
              proficiencyBonus: '+5',
              feature: "Druid Circle feature", 
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            15: {
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            16: {
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement", 
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            17: {
              proficiencyBonus: '+6',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, 1]
            },
            18: {
              proficiencyBonus: '+6',
              feature: "Timeless Body, Beast Spells",
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 3, 1, 1, 1, 1]
            },
            19: {
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 3, 2, 1, 1, 1]
            },
            20: {
              proficiencyBonus: '+6',
              feature: "Archdruid",
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 3, 2, 2, 1, 1]
            }
          },
          similarClasses: {
            firstName: 'Cleric',
            firstDescription: ' Spellcasters, Average Hit Die, Huge Variety Of Healing Spells',
            secondName: 'Ranger',
            secondDescription: ' Similar Lore, Ability to Cast Spells',
          },
          suitableRaces: {
            firstName: 'Human',
            firstDescription: ' +1 to All Ability Scores',
            secondName: 'Half-Elf',
            secondDescription: ' +1 to Two Ability Scores, +2 to Charisma',
          },
        },
        'Monk':{
          name: 'Monk',
          type: 'nonSpellcaster',
          image: "https://i.pinimg.com/564x/a5/ce/6a/a5ce6a1c7e6479c6e2f670e4e89c06e3.jpg",
          introduction: 'Monks are united in their ability to magically harness the energy that flows in their bodies. Whether channeled as a striking display of combat prowess or a subtler focus of defensive ability and speed, this energy infuses all that a monk does. You must have a Dexterity score and a Wisdom score of 13 or higher in order to multiclass in or out of this class.',
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
          },
          levels: {
            1: {
              proficiencyBonus: '+2',
              feature: "Unarmored Defense, Martial Arts",
              martialArts: '1d4',
              kiPoints: '-',
              unarmoredMovement: '-'
            },
            2: {
              proficiencyBonus: '+2',
              feature: "Ki, Unarmored Movement",
              martialArts: '1d4',
              kiPoints: 2,
              unarmoredMovement: '+10ft'
            },
            3: {
              proficiencyBonus: '+2',
              feature: 'Monastic Tradition, Deflect Missiles',
              martialArts: '1d4',
              kiPoints: 3,
              unarmoredMovement: '+10ft'
            },
            4: {
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement, Slow Fall",
              martialArts: '1d4',
              kiPoints: 4,
              unarmoredMovement: '+10ft'
            },
            5: {
              proficiencyBonus: '+3',
              feature: "Extra Attack, Stunning Strike",
              martialArts: '1d6',
              kiPoints: 5,
              unarmoredMovement: '+10ft'
            },
            6: {
              proficiencyBonus: '+3',
              feature: "Ki-Empowered Strikes, Monastic Tradition feature",
              martialArts: '1d6',
              kiPoints: 6,
              unarmoredMovement: '+15ft'
            },
            7: {
              proficiencyBonus: '+3',
              feature: 'Evasion, Stillness of Mind',
              martialArts: '1d6',
              kiPoints: 7,
              unarmoredMovement: '+15ft'
            },
            8: {
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
              martialArts: '1d6',
              kiPoints: 8,
              unarmoredMovement: '+15ft'
            },
            9: {
              proficiencyBonus: '+4',
              feature: 'Unarmored Movement improvement',
              martialArts: '1d6',
              kiPoints: 9,
              unarmoredMovement: '+15ft'
            },
            10: {
              proficiencyBonus: '+4',
              feature: "Purity of Body",
              martialArts: '1d6',
              kiPoints: 10,
              unarmoredMovement: '+20ft'
            },
            11: {
              proficiencyBonus: '+4',
              feature: "Monastic Tradition feature", 
              martialArts: '1d8',
              kiPoints: 11,
              unarmoredMovement: '+20ft'
            },
            12: {
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              martialArts: '1d8',
              kiPoints: 12,
              unarmoredMovement: '+20ft'
            },
            13: {
              proficiencyBonus: '+5',
              feature: 'Tongue of the Sun and Moon',
              martialArts: '1d8',
              kiPoints: 13,
              unarmoredMovement: '+20ft'
            },
            14: {
              proficiencyBonus: '+5',
              feature: "Diamond Soul",
              martialArts: '1d8',
              kiPoints: 14,
              unarmoredMovement: '+25ft'
            },
            15: {
              proficiencyBonus: '+5',
              feature: 'Timeless Body',
              martialArts: '1d8',
              kiPoints: 15,
              unarmoredMovement: '+25ft'
            },
            16: {
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
              martialArts: '1d8',
              kiPoints: 16,
              unarmoredMovement: '+25ft'
            },
            17: {
              proficiencyBonus: '+6',
              feature: "Monastic Tradition feature",
              martialArts: '1d10',
              kiPoints: 17,
              unarmoredMovement: '+25ft'
            },
            18: {
              proficiencyBonus: '+6',
              feature: "Empty Body",
              martialArts: '1d10',
              kiPoints: 18,
              unarmoredMovement: '+30ft'
            },
            19: {
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              martialArts: '1d10',
              kiPoints: 19,
              unarmoredMovement: '+30ft'
            },
            20: {
              proficiencyBonus: '+6',
              feature: "Perfect Self",
              martialArts: '1d10',
              kiPoints: 20,
              unarmoredMovement: '+30ft'
            }
          },       
          similarClasses: {
            firstName: 'Paladin',
            firstDescription: ' Mele Fighters, Both Have a Strong Belief System ',
            secondName: 'Rogue',
            secondDescription: ' Both Require Dexterity, Same Hit Dice, Similar Weapons',
          },
          suitableRaces: {
            firstName: 'Halfling',
            firstDescription: ' +2 Dexterity',
            secondName: 'Elf',
            secondDescription: ' +2 Dexterity',
          },
        },
        'Paladin':{
          name: 'Paladin',
          type: 'halfSpellcaster',
          image: "https://i.pinimg.com/564x/3f/7a/1d/3f7a1d4c8789ac516f6ca0d2dfcd535a.jpg",
          introduction: 'Whether sworn before a god\'s altar and the witness of a priest, in a sacred glade before nature spirits and fey beings, or in a moment of desperation and grief with the dead as the only witness, a paladin\'s oath is a powerful bond. You must have a Charisma score and a Strength score of 13 or higher in order to multiclass in or out of this class.',
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
          },
          levels: {
            1: {
              proficiencyBonus: '+2',
              feature: "Divine Sense, Lay on Hands",
              cantrips: 3,
              spellSlots: ['-', '-', '-', '-', '-']
            },
            2: {
              proficiencyBonus: '+2',
              feature: "Fighting Style, Spellcasting, Divine Smite",
              cantrips: 3,
              spellSlots: [2, '-', '-', '-', '-']
            },
            3: {
              proficiencyBonus: '+2',
              feature: 'Divine Health, Sacred Oath',
              cantrips: 3,
              spellSlots: [3, '-', '-', '-', '-']
            },
            4: {
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [3, '-', '-', '-', '-']
            },
            5: {
              proficiencyBonus: '+3',
              feature: "Extra Attack",
              cantrips: 4,
              spellSlots: [4, 2, '-', '-', '-']
            },
            6: {
              proficiencyBonus: '+3',
              feature: "Aura of Protection",
              cantrips: 4,
              spellSlots: [4, 2, '-', '-', '-']
            },
            7: {
              proficiencyBonus: '+3',
              feature: 'Sacred Oath feature',
              cantrips: 4,
              spellSlots: [4, 3, '-', '-', '-']
            },
            8: {
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [4, 3, '-', '-', '-']
            },
            9: {
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 2, '-', '-']
            },
            10: {
              proficiencyBonus: '+4',
              feature: "Aura of Courage",
              cantrips: 5,
              spellSlots: [4, 3, 2, '-', '-']
            },
            11: {
              proficiencyBonus: '+4',
              feature: "Improved Divine Smite", 
              cantrips: 5,
              spellSlots: [4, 3, 3, '-', '-']
            },
            12: {
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, '-', '-']
            },
            13: {
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 1, '-']
            },
            14: {
              proficiencyBonus: '+5',
              feature: "Cleansing Touch",
              cantrips: 5,
              spellSlots: [4, 3, 3, 1, '-']
            },
            15: {
              proficiencyBonus: '+5',
              feature: 'Sacred Oath feature',
              cantrips: 5,
              spellSlots: [4, 3, 3, 2, '-']
            },
            16: {
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 2, '-']
            },
            17: {
              proficiencyBonus: '+6',
              feature: "",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 1]
            },
            18: {
              proficiencyBonus: '+6',
              feature: "Aura improvements",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 1]
            },
            19: {
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2]
            },
            20: {
              proficiencyBonus: '+6',
              feature: "Sacred Oath feature",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2]
            }
          },
          similarClasses: {
            firstName: 'Monk',
            firstDescription: ' Mele Fighters, Both Have a Strong Belief System ',
            secondName: 'Fighter',
            secondDescription: ' Similar Proficiencies, Fighting Style, Both Require Strength',
          },
          suitableRaces: {
            firstName: 'Half-Elf',
            firstDescription: ' +2 Charisma, +1 to Two Ability Scores',
            secondName: 'Dragonborn',
            secondDescription: ' +2 Strength, +1 Charisma',
          },
        },
        'Ranger':{
          name: 'Ranger',
          type: 'halfSpellcaster',
          image: "https://i.pinimg.com/564x/bf/de/2e/bfde2e3129b297513595c0dc9aea16d2.jpg",
          introduction: 'Far from the bustle of cities and towns, past the hedges that shelter the most distant farms from the terrors of the wild, amid the dense-packed trees of trackless forests and across wide and empty plains, rangers keep their unending watch. You must have a Dexterity score and a Wisdom score of 13 or higher in order to multiclass in or out of this class.',
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
          },
          levels: {
            1: {
              proficiencyBonus: '+2',
              feature: "Favored Enemy, Natural Explorer",
              knownSpells: '-',
              spellSlots: ['-', '-', '-', '-', '-']
            },
            2: {
              proficiencyBonus: '+2',
              feature: "Fighting Style, Spellcasting",
              knownSpells: '2',
              spellSlots: [2, '-', '-', '-', '-']
            },
            3: {
              proficiencyBonus: '+2',
              feature: 'Primeval Awareness, Ranger Conclave',
              knownSpells: '3',
              spellSlots: [3, '-', '-', '-', '-']
            },
            4: {
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              knownSpells: '3',
              spellSlots: [3, '-', '-', '-', '-']
            },
            5: {
              proficiencyBonus: '+3',
              feature: "Ranger Conclave feature",
              knownSpells: '4',
              spellSlots: [4, 2, '-', '-', '-']
            },
            6: {
              proficiencyBonus: '+3',
              feature: "Greater Favored Enemy",
              knownSpells: '4',
              spellSlots: [4, 2, '-', '-', '-']
            },
            7: {
              proficiencyBonus: '+3',
              feature: 'Ranger Conclave feature',
              knownSpells: '5',
              spellSlots: [4, 3, '-', '-', '-']
            },
            8: {
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement, Fleet of Foot",
              knownSpells: '5',
              spellSlots: [4, 3, '-', '-', '-']
            },
            9: {
              proficiencyBonus: '+4',
              feature: '',
              knownSpells: '6',
              spellSlots: [4, 3, 2, '-', '-']
            },
            10: {
              proficiencyBonus: '+4',
              feature: "Hide in Plain Sight",
              knownSpells: '6',
              spellSlots: [4, 3, 2, '-', '-']
            },
            11: {
              proficiencyBonus: '+4',
              feature: "Ranger Conclave feature", 
              knownSpells: '7',
              spellSlots: [4, 3, 3, '-', '-']
            },
            12: {
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              knownSpells: '7',
              spellSlots: [4, 3, 3, '-', '-']
            },
            13: {
              proficiencyBonus: '+5',
              feature: '',
              knownSpells: '8',
              spellSlots: [4, 3, 3, 1, '-']
            },
            14: {
              proficiencyBonus: '+5',
              feature: "Vanish",
              knownSpells: '8',
              spellSlots: [4, 3, 3, 1, '-']
            },
            15: {
              proficiencyBonus: '+5',
              feature: 'Ranger Conclave feature',
              knownSpells: '9',
              spellSlots: [4, 3, 3, 2, '-']
            },
            16: {
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
              knownSpells: '9',
              spellSlots: [4, 3, 3, 2, '-']
            },
            17: {
              proficiencyBonus: '+6',
              feature: "",
              knownSpells: '10',
              spellSlots: [4, 3, 3, 3, 1]
            },
            18: {
              proficiencyBonus: '+6',
              feature: "Feral Senses",
              knownSpells: '10',
              spellSlots: [4, 3, 3, 3, 1]
            },
            19: {
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              knownSpells: '11',
              spellSlots: [4, 3, 3, 3, 2]
            },
            20: {
              proficiencyBonus: '+6',
              feature: "Foe Slayer",
              knownSpells: '11',
              spellSlots: [4, 3, 3, 3, 2]
            }
          },
          similarClasses: {
            firstName: 'Fighter',
            firstDescription: ' Big Hit Die, Both Can Specialise in Archery',
            secondName: 'Druid',
            secondDescription: ' Similar Lore, Ability to Cast Spells',
          },
          suitableRaces: {
            firstName: 'Halfling',
            firstDescription: ' +2 Dexterity',
            secondName: 'Elf',
            secondDescription: ' +2 Dexterity',
          },
        },       
        'Sorcerer':{
          name: 'Sorcerer',
          type: 'Spellcaster',
          image: "https://i.pinimg.com/564x/12/ab/e6/12abe68c7cda152e2a81f9e500c68a02.jpg",
          introduction: 'Sorcerers carry a magical birthright conferred upon them by an exotic bloodline, some otherworldly influence, or exposure to unknown cosmic forces. No one chooses sorcery; the power chooses the sorcerer. You must have a Charisma score of 13 or higher in order to multiclass in or out of this class.',
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
          },
          levels: {
            1: {
              proficiencyBonus: '+2',
              feature: "Spellcasting, Sorcerous Origin",
              knownSpells: 2,
              sorceryPoints: '-',
              cantrips: 4,
              spellSlots: [2, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            2: {
              proficiencyBonus: '+2',
              feature: "Font of Magic",
              knownSpells: 3,
              sorceryPoints: 2,
              cantrips: 4,
              spellSlots: [3, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            3: {
              proficiencyBonus: '+2',
              feature: 'Metamagic',
              knownSpells: 4,
              sorceryPoints: 3,
              cantrips: 4,
              spellSlots: [4, 2, '-', '-', '-', '-', '-', '-', '-']
            },
            4: {
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              knownSpells: 5,
              sorceryPoints: 4,
              cantrips: 5,
              spellSlots: [4, 3, '-', '-', '-', '-', '-', '-', '-']
            },
            5: {
              proficiencyBonus: '+3',
              feature: '',
              knownSpells: 6,
              sorceryPoints: 5,
              cantrips: 5,
              spellSlots: [4, 3, 2, '-', '-', '-', '-', '-', '-']
            },
            6: {
              proficiencyBonus: '+3',
              feature: "Sorcerous Origin feature", 
              knownSpells: 7,
              sorceryPoints: 6,
              cantrips: 5,
              spellSlots: [4, 3, 3, '-', '-', '-', '-', '-', '-']
            },
            7: {
              proficiencyBonus: '+3',
              feature: '',
              knownSpells: 8,
              sorceryPoints: 7,
              cantrips: 5,
              spellSlots: [4, 3, 3, 1, '-', '-', '-', '-', '-']
            },
            8: {
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
              knownSpells: 9,
              sorceryPoints: 8,
              cantrips: 5,
              spellSlots: [4, 3, 3, 2, '-', '-', '-', '-', '-']
            },
            9: {
              proficiencyBonus: '+4',
              feature: '',
              knownSpells: 10,
              sorceryPoints: 9,
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 1, '-', '-', '-', '-']
            },
            10: {
              proficiencyBonus: '+4',
              feature: "Metamagic",
              knownSpells: 11,
              sorceryPoints: 10,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, '-', '-', '-', '-']
            },
            11: {
              proficiencyBonus: '+4',
              feature: '',
              knownSpells: 12,
              sorceryPoints: 11,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            12: {
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              knownSpells: 12,
              sorceryPoints: 12,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            13: {
              proficiencyBonus: '+5',
              feature: '',
              knownSpells: 13,
              sorceryPoints: 13,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            14: {
              proficiencyBonus: '+5',
              feature: 'Sorcerous Origin feature',
              knownSpells: 13,
              sorceryPoints: 14,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            15: {
              proficiencyBonus: '+5',
              feature: '',
              knownSpells: 14,
              sorceryPoints: 15,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            16: {
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement", 
              knownSpells: 14,
              sorceryPoints: 16,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            17: {
              proficiencyBonus: '+6',
              feature: 'Metamagic',
              knownSpells: 15,
              sorceryPoints: 17,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, 1]
            },
            18: {
              proficiencyBonus: '+6',
              feature: "Sorcerous Origin feature",
              knownSpells: 15,
              sorceryPoints: 18,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 3, 1, 1, 1, 1]
            },
            19: {
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              knownSpells: 15,
              sorceryPoints: 19,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 3, 2, 1, 1, 1]
            },
            20: {
              proficiencyBonus: '+6',
              feature: "Sorcerous Restoration",
              knownSpells: 15,
              sorceryPoints: 20,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 3, 2, 2, 1, 1]
            }
          },
            similarClasses: {
            firstName: 'Wizard',
            firstDescription: ' Spellcasters, No Armor, Small Hit Die, Huge Variety Of Spells',
            secondName: 'Bard',
            secondDescription: ' Spellcasters, Huge Variety Of Spells',
            },
            suitableRaces: {
              firstName: 'Half-Elf',
              firstDescription: ' +2 Charisma, +1 to Two Ability Scores',
              secondName: 'Tiefling',
              secondDescription: ' +2 Charisma',
            },
        },
        'Warlock':{
          name: 'Warlock',
          type: 'invocationSpellcaster',
          image: "https://i.pinimg.com/564x/95/e9/9d/95e99d65e126b63e3daf5b590ca23b00.jpg",
          introduction: 'Warlocks are seekers of the knowledge that lies hidden in the fabric of the multiverse. Through pacts made with mysterious beings of supernatural power, warlocks unlock magical effects both subtle and spectacular. You must have a Charisma score of 13 or higher in order to multiclass in or out of this class.',
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
          },
          levels: {
            1: {
              proficiencyBonus: '+2',
              feature: "Otherworldly Patron, Pact Magic",
              cantrips: 2,
              knownSpells: 2,
              warlockSpellSlots: 1,
              warlockSlotLevel: '1st',
              warlockInvocations: '-'
            },
            2: {
              proficiencyBonus: '+2',
              feature: "Eldritch Invocations",
              cantrips: 2,
              knownSpells: 3,
              warlockSpellSlots: 2,
              warlockSlotLevel: '1st',
              warlockInvocations: '2'
            },
            3: {
              proficiencyBonus: '+2',
              feature: 'Pact Boon',
              cantrips: 2,
              knownSpells: 4,
              warlockSpellSlots: 2,
              warlockSlotLevel: '2nd',
              warlockInvocations: '2'
            },
            4: {
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              cantrips: 3,
              knownSpells: 5,
              warlockSpellSlots: 2,
              warlockSlotLevel: '2nd',
              warlockInvocations: '2'
            },
            5: {
              proficiencyBonus: '+3',
              feature: "",
              cantrips: 3,
              knownSpells: 6,
              warlockSpellSlots: 2,
              warlockSlotLevel: '3rd',
              warlockInvocations: '3'
            },
            6: {
              proficiencyBonus: '+3',
              feature: "Otherworldly Patron feature",
              cantrips: 3,
              knownSpells: 7,
              warlockSpellSlots: 2,
              warlockSlotLevel: '3rd',
              warlockInvocations: '3'
            },
            7: {
              proficiencyBonus: '+3',
              feature: '',
              cantrips: 3,
              knownSpells: 8,
              warlockSpellSlots: 2,
              warlockSlotLevel: '4th',
              warlockInvocations: '4'
            },
            8: {
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
              cantrips: 3,
              knownSpells: 9,
              warlockSpellSlots: 2,
              warlockSlotLevel: '4th',
              warlockInvocations: '4'
            },
            9: {
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 3,
              knownSpells: 10,
              warlockSpellSlots: 2,
              warlockSlotLevel: '5th',
              warlockInvocations: '5'
            },
            10: {
              proficiencyBonus: '+4',
              feature: "Otherworldly Patron feature",
              cantrips: 4,
              knownSpells: 10,
              warlockSpellSlots: 2,
              warlockSlotLevel: '5th',
              warlockInvocations: '5'
            },
            11: {
              proficiencyBonus: '+4',
              feature: "Mystic Arcanum (6th level)",
              cantrips: 4, 
              knownSpells: 11,
              warlockSpellSlots: 3,
              warlockSlotLevel: '5th',
              warlockInvocations: '5'
            },
            12: {
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              cantrips: 4,
              knownSpells: 11,
              warlockSpellSlots: 3,
              warlockSlotLevel: '5th',
              warlockInvocations: '6'
            },
            13: {
              proficiencyBonus: '+5',
              feature: 'Mystic Arcanum (7th level)',
              cantrips: 4,
              knownSpells: 12,
              warlockSpellSlots: 3,
              warlockSlotLevel: '5th',
              warlockInvocations: '6'
            },
            14: {
              proficiencyBonus: '+5',
              feature: "Otherworldly Patron feature",
              cantrips: 4,
              knownSpells: 12,
              warlockSpellSlots: 3,
              warlockSlotLevel: '5th',
              warlockInvocations: '6'
            },
            15: {
              proficiencyBonus: '+5',
              feature: 'Mystic Arcanum (8th level)',
              cantrips: 4,
              knownSpells: 13,
              warlockSpellSlots: 3,
              warlockSlotLevel: '5th',
              warlockInvocations: '7'
            },
            16: {
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
              cantrips: 4,
              knownSpells: 13,
              warlockSpellSlots: 3,
              warlockSlotLevel: '5th',
              warlockInvocations: '7'
            },
            17: {
              proficiencyBonus: '+6',
              feature: "Mystic Arcanum (9th level)",
              cantrips: 4,
              knownSpells: 14,
              warlockSpellSlots: 4,
              warlockSlotLevel: '5th',
              warlockInvocations: '7'
            },
            18: {
              proficiencyBonus: '+6',
              feature: "",
              cantrips: 4,
              knownSpells: 14,
              warlockSpellSlots: 4,
              warlockSlotLevel: '5th',
              warlockInvocations: '8'
            },
            19: {
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              cantrips: 4,
              knownSpells: 15,
              warlockSpellSlots: 4,
              warlockSlotLevel: '5th',
              warlockInvocations: '8'
            },
            20: {
              proficiencyBonus: '+6',
              feature: "Eldritch Master",
              cantrips: 4,
              knownSpells: 15,
              warlockSpellSlots: 4,
              warlockSlotLevel: '5th',
              warlockInvocations: '8'
            }
          },
          similarClasses: {
            firstName: 'Barbarian',
            firstDescription: ' Both Require Strength, Similar Aesthetic',
            secondName: 'Paladin',
            secondDescription: ' Similar Proficiencies, Fighting Style, Both Require Strength',
          },
          suitableRaces: {
            firstName: 'Half-Orc',
            firstDescription: ' +2 Strength',
            secondName: 'Dragonborn',
            secondDescription: ' +2 Strength',
          },
        },
        'Bard':{
          name: 'Bard',
          type: 'Spellcaster',
          image: "https://i.pinimg.com/564x/ff/0b/90/ff0b907eec84bb483ad612093514dc56.jpg",
          introduction: 'Whether scholar, skald, or scoundrel, a bard weaves magic through words and music to inspire allies, demoralize foes, manipulate minds, create illusions, and even heal wounds. The bard is a master of song, speech, and the magic they contain. You must have a Charisma score of 13 or higher in order to multiclass in or out of this class.',
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
          },
          levels: {
            1: {
              proficiencyBonus: '+2',
              feature: "Spellcasting, Bardic Inspiration (d6)",
              knownSpells: 4,
              cantrips: 2,
              spellSlots: [2, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            2: {
              proficiencyBonus: '+2',
              feature: "Jack of All Trades, Song of Rest (d6)",
              knownSpells: 5,
              cantrips: 2,
              spellSlots: [3, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            3: {
              proficiencyBonus: '+2',
              feature: 'Bard College, Expertise',
              knownSpells: 6,
              cantrips: 2,
              spellSlots: [4, 2, '-', '-', '-', '-', '-', '-', '-']
            },
            4: {
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              knownSpells: 7,
              cantrips: 3,
              spellSlots: [4, 3, '-', '-', '-', '-', '-', '-', '-']
            },
            5: {
              proficiencyBonus: '+3',
              feature: 'Bardic Inspiration (d8), Font of Inspiration',
              knownSpells: 8,
              cantrips: 3,
              spellSlots: [4, 3, 2, '-', '-', '-', '-', '-', '-']
            },
            6: {
              proficiencyBonus: '+3',
              feature: "Countercharm, Bard College feature", 
              knownSpells: 9,
              cantrips: 3,
              spellSlots: [4, 3, 3, '-', '-', '-', '-', '-', '-']
            },
            7: {
              proficiencyBonus: '+3',
              feature: '',
              knownSpells: 10,
              cantrips: 3,
              spellSlots: [4, 3, 3, 1, '-', '-', '-', '-', '-']
            },
            8: {
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
              knownSpells: 11,
              cantrips: 3,
              spellSlots: [4, 3, 3, 2, '-', '-', '-', '-', '-']
            },
            9: {
              proficiencyBonus: '+4',
              feature: 'Song of Rest (d8)',
              knownSpells: 12,
              cantrips: 3,
              spellSlots: [4, 3, 3, 3, 1, '-', '-', '-', '-']
            },
            10: {
              proficiencyBonus: '+4',
              feature: "Bardic Inspiration (d10), Expertise, Magical Secrets",
              knownSpells: 14,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, '-', '-', '-', '-']
            },
            11: {
              proficiencyBonus: '+4',
              feature: '',
              knownSpells: 15,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            12: {
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              knownSpells: 15,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            13: {
              proficiencyBonus: '+5',
              feature: 'Song of Rest (d10)',
              knownSpells: 16,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            14: {
              proficiencyBonus: '+5',
              feature: 'Magical Secrets, Bard College feature',
              knownSpells: 18,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            15: {
              proficiencyBonus: '+5',
              feature: 'Bardic Inspiration (d12)',
              knownSpells: 19,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            16: {
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement", 
              knownSpells: 19,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            17: {
              proficiencyBonus: '+6',
              feature: 'Song of Rest (d12)',
              knownSpells: 20,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, 1]
            },
            18: {
              proficiencyBonus: '+6',
              feature: "Magical Secrets",
              knownSpells: 22,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 3, 1, 1, 1, 1]
            },
            19: {
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              knownSpells: 22,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 3, 2, 1, 1, 1]
            },
            20: {
              proficiencyBonus: '+6',
              feature: "Superior Inspiration",
              knownSpells: 22,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 3, 2, 2, 1, 1]
            }
          },
            similarClasses: {
            firstName: 'Wizard',
            firstDescription: ' Spellcasters, No Armor, Small Hit Die, Huge Variety Of Spells',
            secondName: 'Sorcerer',
            secondDescription: ' Spellcasters, Huge Variety Of Spells, Both Require Charisma',
            },
            suitableRaces: {
              firstName: 'Half-Elf',
              firstDescription: ' +2 Charisma, +1 to Two Ability Scores',
              secondName: 'Tiefling',
              secondDescription: ' +2 Charisma',
            },
        },
        'Barbarian':{
          name: 'Barbarian',
          type: 'nonSpellcaster',
          image: "https://i.pinimg.com/564x/4a/a0/b7/4aa0b7c762d03855391f8c40ab140b6e.jpg",
          introduction: 'For some, their rage springs from a communion with fierce animal spirits. Others draw from a roiling reservoir of anger at a world full of pain. For every barbarian, rage is a power that fuels not just a battle frenzy but also uncanny reflexes, resilience, and feats of strength. You must have a Strength score of 13 or higher in order to multiclass in or out of this class.',
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
          },
          levels: {
            1: {
              proficiencyBonus: '+2',
              rage: 2,
              rageDamage: '+2',
              feature: "Rage, Unarmored Defense",
            },
            2: {
              proficiencyBonus: '+2',
              rage: 2,
              rageDamage: '+2',
              feature: "Reckless Attack, Danger Sense",
            },
            3: {
              proficiencyBonus: '+2',
              rage: 3,
              rageDamage: '+2',
              feature: 'Primal Path',
            },
            4: {
              proficiencyBonus: '+2',
              rage: 3,
              rageDamage: '+2',
              feature: "Ability Score Improvement",
            },
            5: {
              proficiencyBonus: '+3',
              rage: 3,
              rageDamage: '+2',
              feature: "Extra Attack, Fast Movement",
            },
            6: {
              proficiencyBonus: '+3',
              rage: 4,
              rageDamage: '+2',
              feature: "Path feature",
            },
            7: {
              proficiencyBonus: '+3',
              rage: 4,
              rageDamage: '+2',
              feature: 'Feral Instinct',
            },
            8: {
              proficiencyBonus: '+3',
              rage: 4,
              rageDamage: '+2',
              feature: "Ability Score Improvement",
            },
            9: {
              proficiencyBonus: '+4',
              rage: 4,
              rageDamage: '+3',
              feature: 'Brutal Critical (1 die)',
            },
            10: {
              proficiencyBonus: '+4',
              rage: 4,
              rageDamage: '+3',
              feature: "Path feature",
            },
            11: {
              proficiencyBonus: '+4',
              rage: 4,
              rageDamage: '+3',
              feature: "Relentless Rage", 
            },
            12: {
              proficiencyBonus: '+4',
              rage: 5,
              rageDamage: '+3',
              feature: "Ability Score Improvement",
            },
            13: {
              proficiencyBonus: '+5',
              rage: 5,
              rageDamage: '+3',
              feature: 'Brutal Critical (2 dice)',
            },
            14: {
              proficiencyBonus: '+5',
              rage: 5,
              rageDamage: '+3',
              feature: "Path feature",
            },
            15: {
              proficiencyBonus: '+5',
              rage: 5,
              rageDamage: '+3',
              feature: 'Persistent Rage',
            },
            16: {
              proficiencyBonus: '+5',
              rage: 5,
              rageDamage: '+4',
              feature: "Ability Score Improvement",
            },
            17: {
              proficiencyBonus: '+6',
              rage: 6,
              rageDamage: '+4',
              feature: "Brutal Critical (3 dice)",
            },
            18: {
              proficiencyBonus: '+6',
              rage: 6,
              rageDamage: '+4',
              feature: "Indomitable Might",
            },
            19: {
              proficiencyBonus: '+6',
              rage: 6,
              rageDamage: '+4',
              feature: "Ability Score Improvement",
            },
            20: {
              proficiencyBonus: '+6',
              rage: 'Unlimited',
              rageDamage: '+4',
              feature: "Primal Champion",
            }
          },
          similarClasses: {
            firstName: 'Fighter',
            firstDescription: ' Both Require Strength, Similar Aesthetic, Similar Weapons',
            secondName: 'Paladin',
            secondDescription: ' Both Require Strength, Similar Weapons',
          },
          suitableRaces: {
            firstName: 'Half-Orc',
            firstDescription: ' +2 Strength',
            secondName: 'Dragonborn',
            secondDescription: ' +2 Strength',
          },
        },
      },
      allRaces:{
        'Dragonborn':{
          name: 'Dragonborn',
          image: 'https://i.pinimg.com/236x/7d/8b/b1/7d8bb1e0f6e896d456871171891b73e1.jpg',
          introduction: 'The dragonborn walk proudly through a world that greets them with fearful incomprehension. Shaped by the dragons themselves, dragonborn originally hatched from dragon eggs as a unique race, combining the best attributes of dragons and humanoids.',
          age: 'Young dragonborn grow quickly. They walk hours after hatching, attain the size and development of a 10-year-old human child by the age of 3, and reach adulthood by 15. They live to be around 80.',
          alignment: 'Dragonborn tend towards extremes, making a conscious choice for one side or the other between Good and Evil (represented by Bahamut and Tiamat, respectively). More side with Bahamut than Tiamat (whose non-dragon followers are mostly kobolds), but villainous dragonborn can be quite terrible indeed. Some rare few choose to devote themselves to lesser dragon deities, such as Chronepsis (Neutral), and fewer still choose to worship Io, the Ninefold Dragon, who is all alignments at once.',
          size: 'Dragonborn are taller and heavier than humans, standing well over 6 feet tall and averaging almost 250 pounds. Your size is Medium.',
          speed: 'Your base walking speed is 30 feet.',
          languages: 'You can read, speak, and write Common and Draconic.',
          abilityScoreIncrease: 'Your Strength score increases by 2, and your Charisma score increases by 1.',
          similarRaces: {
            firstName: 'Half-Orc',
            firstDescription: ' +2 Strength',
            secondName: 'Tiefling',
            secondDescription: ' +2 Charisma',
          },
          suitableClasses: {
            firstName: 'Fighter',
            firstDescription: ' Strength is a Primary Ability for a Fighter',
            secondName: 'Bard',
            secondDescription: ' Charisma is a Primary Ability for a Bard',
          },
        },
        'Dwarf':{
          name: 'Dwarf',
          image: 'https://i.pinimg.com/236x/94/79/3b/94793b0a60d5d635cd8f5fce25006a71.jpg',
          introduction: 'Kingdoms rich in ancient grandeur, halls carved into the roots of mountains, the echoing of picks and hammers in deep mines and blazing forges, a commitment to clan and tradition, and a burning hatred of goblins and orcs – these common threads unite all dwarves.',
          age: 'Dwarves mature at the same rate as humans, but they\'re considered young until they reach the age of 50. On average, they live about 350 years.',
          alignment: 'Most dwarves are lawful, believing firmly in the benefits of a well-ordered society. They tend toward good as well, with a strong sense of fair play and a belief that everyone deserves to share in the benefits of a just order.',
          size: 'Dwarves stand between 4 and 5 feet tall and average about 150 pounds. Your size is Medium.',
          speed: 'Your base walking speed is 25 feet. Your speed is not reduced by wearing heavy armor.',
          languages: 'You can speak, read, and write Common and Dwarvish. Dwarvish is full of hard consonants and guttural sounds, and those characteristics spill over into whatever other language a dwarf might speak.',
          abilityScoreIncrease: 'Your Constitution score increases by 2.',
          similarRaces: {
            firstName: 'Human',
            firstDescription: ' +1 to All Ability Scores',
            secondName: 'Half-Elf',
            secondDescription: ' +1 to Two Ability Scores, +2 to Charisma',
          },
          suitableClasses: {
            firstName: 'Fighter',
            firstDescription: ' Mele Classes Need Constitution the Most',
            secondName: 'Barbarian',
            secondDescription: ' Mele Classes Need Constitution the Most',
          },
        },
        'Elf':{
          name: 'Elf',
          image: 'https://i.pinimg.com/564x/5d/b8/23/5db823eebc80060458d7f23529bac729.jpg',
          introduction: 'Elves are a magical people of otherworldly grace, living in places of ethereal beauty, in the midst of ancient forests or in silvery spires glittering with faerie light, where soft music drifts through the air and gentle fragrances waft on the breeze. Elves love nature and magic, art and artistry, music and poetry.',
          age: 'Although elves reach physical maturity at about the same age as humans, the elven understanding of adulthood goes beyond physical growth to encompass worldly experience. An elf typically claims adulthood and an adult name around the age of 100 and can live to be 750 years old.',
          alignment: 'Elves love freedom, variety, and self-expression, so they lean strongly towards the gentler aspects of chaos. They value and protect others\' freedom as well as their own, and are good more often than not. Drow are an exception; their exile into the Underdark has made them vicious and dangerous. Drow are more often evil than not.',
          size: 'Elves range from under 5 to over 6 feet tall and have slender builds. Your size is Medium.',
          speed: 'Your base walking speed is 30 feet.',
          languages: 'You can speak, read, and write Common and Elven.',
          abilityScoreIncrease: 'Your Dexterity score increases by 2.',
          similarRaces: {
            firstName: 'Halfling',
            firstDescription: ' +2 Dexterity',
            secondName: 'Half-Elf',
            secondDescription: ' +1 to Two Ability Scores, +2 to Charisma',
          },
          suitableClasses: {
            firstName: 'Rogue',
            firstDescription: ' Dexterity is a Primary Ability for a Rogue',
            secondName: 'Ranger',
            secondDescription: ' Dexterity is a Primary Ability for a Ranger',
          },
        },
        'Gnome':{
          name: 'Gnome',
          image: 'https://i.pinimg.com/236x/99/26/ca/9926ca7ef998c98e40a06df29dc8b3bf.jpg',
          introduction: 'A constant hum of busy activity pervades the warrens and neighborhoods where gnomes form their close-knit communities. Louder sounds punctuate the hum: a crunch of grinding gears here, a minor explosion there, a yelp of surprise or triumph, and especially bursts of laughter. Gnomes take delight in life, enjoying every moment of invention, exploration, investigation, creation, and play.',
          age: 'Gnomes mature at the same rate as humans, and most are expected to settle into adult life around the age of 40. They can live to 350 years on average, but it\'s not too uncommon for them to reach 500 years of age.',
          alignment: 'Gnomes are generally Good. Those who tend towards Law are sages, engineers, researchers, scholars, investigators, or inventors. Those who tend towards Chaos are often minstrels, tricksters, wanderers, or fanciful jewelers. Gnomes are light-hearted, and even the tricksters amongst them favor harmless pranks over vicious schemes.',
          size: 'Gnomes are between 3 and 4 feet tall and weigh around 40 pounds. Your size is Small.',
          speed: 'Your base walking speed is 25 feet.',
          languages: 'You can read, speak, and write Common and Gnomish.',
          abilityScoreIncrease: 'Your Intelligence score increases by 2.',
          similarRaces: {
            firstName: 'Tiefling',
            firstDescription: ' +2 Intelligence',
            secondName: 'Half-Elf',
            secondDescription: ' +1 to Two Ability Scores, +2 to Charisma',
          },
          suitableClasses: {
            firstName: 'Wizard',
            firstDescription: ' Intelligence is a Primary Ability for a Wizard',
            secondName: 'Rogue',
            secondDescription: ' Your Small Size Gives You Advantage on Your Stealth Checks',
          },
        },
        'Half-Elf':{
          name: 'Half-Elf',
          image: 'https://i.pinimg.com/236x/78/1c/78/781c78e04b2049b19f71335f1f8698ec.jpg',
          introduction: 'Walking in two worlds but truly belonging to neither, half-elves combine what some say are the best qualities of their elf and human parents: human curiosity, inventiveness, and ambition tempered by the refined senses, love of nature, and artistic tastes of the elves.',
          age: 'Half-elves age at much the same rate as humans, reaching adulthood at the age of 20. They live much longer than humans, however, often exceeding 180 years.',
          alignment: 'Half-elves share the chaotic bent of their elven heritage. They both value personal freedom and creative expression, demonstrating neither love of leaders nor desire for followers. They chafe at rules, resent others\' demands, and sometimes prove unreliable, or at least unpredictable. They are good and evil in equal numbers, a trait they share with their human parents.',
          size: 'Half-elves are more or less the same size as humans, ranging from 5 to 6 feet tall. Your size is Medium.',
          speed: 'Your base walking speed is 30 feet.',
          languages: 'You can read, speak, and write Common, Elven, and one language of your choice.',
          abilityScoreIncrease: 'Your Charisma score increases by 2, and two other ability scores of your choice each increase by 1.',
          similarRaces: {
            firstName: 'Tiefling',
            firstDescription: ' +2 Charisma',
            secondName: 'Dragonborn',
            secondDescription: ' +1 Charisma',
          },
          suitableClasses: {
            firstName: 'Sorcerer',
            firstDescription: ' Charisma is a Primary Ability for a Sorcerer',
            secondName: 'Paladin',
            secondDescription: ' Charisma is a Primary Ability for a Paladin',
          },
        },
        'Half-Orc':{
          name: 'Half-Orc',
          image: 'https://i.pinimg.com/236x/72/26/e5/7226e55385fdce0cb4105821fc8994b4.jpg',
          introduction: 'When alliances between humans and orcs are sealed by marriages, half-orcs are born. Some half-orcs rise to become proud chiefs of orc tribes, their human blood giving them an edge over their full-blooded orc rivals. Some venture into the world to prove their worth among humans and other more civilized races. Many of these become adventurers, achieving greatness for their mighty deeds and notoriety for their barbaric customs and savage fury.',
          age: 'Half-orcs mature a little faster than humans, reaching adulthood around age 14. They age noticeably faster and rarely live longer than 75 years.',
          alignment: 'Half-orcs inherit a tendency toward chaos from their orc parents and are not strongly inclined toward good. Half-orcs raised among orcs and willing to live out their lives among them are usually evil.',
          size: 'Half-orcs are somewhat larger and bulkier than humans, and they range from 5 to well over 6 feet tall. Your size is Medium.',
          speed: 'Your base walking speed is 30 feet.',
          languages: 'You can speak, read, and write Common and Orc. Orc is a harsh, grating language with hard consonants. It has no script of its own but is written in the Dwarvish script.',
          abilityScoreIncrease: 'Your Strength score increases by 2, and your Constitution score increases by 1.',
          similarRaces: {
            firstName: 'Dragonborn',
            firstDescription: ' +2 Strength',
            secondName: 'Dwarf',
            secondDescription: ' +2 Constitution',
          },
          suitableClasses: {
            firstName: 'Fighter',
            firstDescription: ' Strength is a Primary Ability for a Fighter',
            secondName: 'Barbarian',
            secondDescription: ' Strength is a Primary Ability for a Barbarian',
          },
        },
        'Halfling':{
          name: 'Halfling',
          image: 'https://i.pinimg.com/236x/72/81/0b/72810b2b7c8909ac6c5636088ebd26f7.jpg',
          introduction: 'The comforts of home are the goals of most halflings\' lives: a place to settle in peace and quiet, far from marauding monsters and clashing armies. Others form nomadic bands that travel constantly, lured by the open road and the wide horizon to discover the wonders of new lands and peoples. Halflings work readily with others, and they are loyal to their friends, whether halfling or otherwise. They can display remarkable ferocity when their friends, families, or communities are threatened.',
          age: 'A halfling reaches adulthood at the age of 20 and generally lives into the middle of his or her second century.',
          alignment: 'Most halflings are lawful good. As a rule, they are good-hearted and kind, hate to see others in pain, and have no tolerance for oppression. They are also very orderly and traditional, leaning heavily on the support of their community and the comfort of the old ways.',
          size: 'Halflings average about 3 feet tall and weigh about 40 pounds. Your size is small.',
          speed: 'Your base walking speed is 25 feet.',
          languages: 'You can speak, read, and write Common and Halfling.',
          abilityScoreIncrease: 'Your Dexterity score increases by 2.',
          similarRaces: {
            firstName: 'Elf',
            firstDescription: ' +2 Dexterity',
            secondName: 'Half-Elf',
            secondDescription: ' +1 to Two Ability Scores, +2 to Charisma',
          },
          suitableClasses: {
            firstName: 'Monk',
            firstDescription: ' Dexterity is a Primary Ability for a Monk',
            secondName: 'Ranger',
            secondDescription: ' Dexterity is a Primary Ability for a Ranger',
          },
        },
        'Human':{
          name: 'Human',
          image: 'https://i.pinimg.com/236x/05/6f/61/056f6147337010aed86ffabe25687f37.jpg',
          introduction: 'In the reckonings of most worlds, humans are the youngest of the common races, late to arrive on the world scene and short-lived in comparison to dwarves, elves, and dragons. Perhaps it is because of their shorter lives that they strive to achieve as much as they can in the years they are given. Or maybe they feel they have something to prove to the elder races, and that\'s why they build their mighty empires on the foundation of conquest and trade. Whatever drives them, humans are the innovators, the achievers, and the pioneers of the worlds.',
          age: 'Humans reach adulthood in their late teens and live less than a century.',
          alignment: 'Humans tend toward no particular alignment. The best and the worst are found among them.',
          size: 'Humans vary widely in height and build, from barely 5 feet to well over 6 feet tall. Regardless of your position in that range, your size is Medium.',
          speed: 'Your base walking speed is 30 feet.',
          languages: 'You can speak, read, and write Common and one extra language of your choice. Humans typically learn the languages of other peoples they deal with, including obscure dialects. They are fond of sprinkling their speech with words borrowed from other tongues: Orc curses, Elvish musical expressions, Dwarvish military phrases, and so on.',
          abilityScoreIncrease: 'Your ability scores each increase by 1.',
          similarRaces: {
            firstName: 'Dragonborn',
            firstDescription: ' +2 Strength, +1 Charisma',
            secondName: 'Half-Elf',
            secondDescription: ' +1 to Two Ability Scores, +2 to Charisma',
          },
          suitableClasses: {
            firstName: 'Monk',
            firstDescription: ' Has Two Primary Abilities: Wisdom and Dexterity',
            secondName: 'Paladin',
            secondDescription: ' Has Two Primary Abilities: Strength and Charisma',
          },
        },
        'Tiefling':{
          name: 'Tiefling',
          image: 'https://i.pinimg.com/236x/15/36/1b/15361b13b8a28d959bfbe1c249e86c8a.jpg',
          introduction: 'To be greeted with stares and whispers, to suffer violence and insult on the street, to see mistrust and fear in every eye: this is the lot of the tiefling. And to twist the knife, tieflings know that this is because a pact struck generations ago infused the essence of Asmodeus, overlord of the Nine Hells (and many of the other powerful devils serving under him) into their bloodline. Their appearance and their nature are not their fault but the result of an ancient sin, for which they and their children and their children\'s children will always be held accountable.',
          age: 'Tieflings mature at the same rate as humans but live a few years longer.',
          alignment: 'Tieflings might not have an innate tendency toward evil, but many of them end up there. Evil or not, an independent nature inclines many tieflings toward a chaotic alignment.',
          size: 'Tieflings are about the same size and build as humans. Your size is Medium.',
          speed: 'Your base walking speed is 30 feet.',
          languages: 'You can speak, read, and write Common and Infernal.',
          abilityScoreIncrease: 'Your Charisma score increases by 2.',
          similarRaces: {
            firstName: 'Half-Elf',
            firstDescription: ' +2 Charisma',
            secondName: 'Dragonborn',
            secondDescription: ' +1 Charisma',
          },
          suitableClasses: {
            firstName: 'Warlock',
            firstDescription: ' Charisma is a Primary Ability for a Warlock',
            secondName: 'Bard',
            secondDescription: ' Charisma is a Primary Ability for a Bard',
          },
        }
      },
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
    },
    chooseRace(chosenRace){
      this.pageChanger = chosenRace;
      console.log(this.pageChanger);
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
   },
   finalChoiceOfRace(finalRacename){
      this.finalRace = finalRacename;
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
            console.log(result1);
            result2 = oneWord.slice(i).join('');
            console.log(result2);
            finalWords = result1 + ' ' + result2;
            console.log(finalWords);
         }
     }

     if(finalWords == ''){
       finalWords = oneWord.join('');
     }
     
     return finalWords;
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
html, body, .col-6{
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
.all-classes-page-title, .all-races-page-title{
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
.dnd-classes-title, .dnd-races-title{
  margin-left: -9%;
  color: #151515;
}
.all-classes, .all-races{
  background-color: #3f473a;
}
.btn-primary{
  color: #989a9c;
  font-weight: bold;
  background-color: #462025;
  border-color: #462025;
}
.btn-primary:hover, .btn-primary:active{
  background-color: #584447;
  border-color:  #2b1417; 
}
html{
  background-color: #3f473a;
}
h2,h3,h4{
  color: #000;
}
.classes-sidebar-recommendations, .races-sidebar-recommendations{
  background-color: #3e3731;
  border-left: 2px solid #151515 !important;
  border-right: 2px solid #151515!important;
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
.class-title-on-class-page, .race-title-on-race-page{
   color: #151515;
   font-weight: bold;
}
.class-detailed-description, .race-detailed-description{
  text-align: left;
}
.class-table{
  height: 75%;
}
.class-detailed-description-title{
  color: #000;
  padding-bottom: 30px;
}
.race-detailed-description-title{
  font-weight: bold;
  color: #151515;
}
.class-detailed-description-mini-title{
  color: #000;
  font-weight: bold;
}
.race-detailed-description-mini-title{
  font-weight: bold;
  color: #151515;
}
.class-mini-description-on-class-page{
   text-align: left;
   font-weight: bold;
}
.race-mini-description-on-race-page{
  text-align: left;
  font-weight: bold;
  padding-bottom: 40px;
}
.header-of-class-table th {
    color:rgb(20, 19, 19) !important;
}
.secondary-header-of-class-table th {
    color:rgb(20, 19, 19) !important;
}
.dnd-class-table{
   color:rgb(27, 27, 27) !important;
   font-weight: bold !important;
}
.dnd-class-table th{
   border-top: 1px solid #6c7075 !important;
}
.dnd-class-table td{
   border-top: 1px solid #6c7075 !important;
}
.dnd-class-table thead th {
    border-bottom: 2px solid #6c7075 !important;
}
.similar-classes, .suitable-races, .similar-races, .suitable-classes{
  padding-bottom: 7px;
  padding-top: 50px;
  color: #151515;
  font-weight: bold;
}
.similar-classes-example, .suitable-races-example, .similar-races-example, .suitable-classes-example{
  padding-top: 20px;
  color: #15191d;
  font-weight: bold;
}
.suitable-races-example-description, .similar-classes-example-description, .suitable-classes-example-description, .similar-races-example-description{
  color: #15191d;
}
.classes-main-description, .races-main-description{
  padding-right: 30px;
  padding-top: 40px;
}
.class-detailed-description{
  padding-top: 30px;
  padding-bottom: 50px;
}
.race-page{
  height: 100%;
}
.initial-select{
  height: 100%;
}
.classes-container, .races-container{
  background-color:  #3e3731;
}
</style>