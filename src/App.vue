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
      <div class="container all-classes" v-if="pageChanger === 'allClasses'">
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
        <div class="row" v-if="pageChanger === 'allRaces'">
            <div class="container all-races">
                <div class="row all-races-page-title">
                    <h1 class="dnd-races-title">Races</h1>
                </div>
                <div class="row all-races-page-thumbnails">
                    <div v-for="dndClass in allClasses" :key="dndClass.name" class="figure col-3">
                        <img :src="dndClass.image" class="figure-img img-fluid rounded img-classes-thumbnails" alt="A generic square placeholder image with rounded corners in a figure.">
                        <button v-on:click="chooseClass(dndClass.name)" type="button" class="btn btn-primary" data-toggle="button" aria-pressed="false" autocomplete="off">{{dndClass.name}}</button>
                    </div>
                </div>
            </div>
        </div>
        <div class="container" v-if="pageChanger === 'Wizard' || pageChanger === 'Cleric' || pageChanger === 'Druid' || pageChanger === 'Fighter' || pageChanger === 'Rogue' || pageChanger === 'Barbarian' || pageChanger === 'Warlock' || pageChanger === 'Ranger' || pageChanger === 'Paladin' || pageChanger === 'Monk' || pageChanger === 'Sorcerer' || pageChanger === 'Bard'">
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
                    </tr>
                  </thead>
                  <thead class="thead-dark secondary-header-of-class-table">
                    <tr>
                      <th scope="col">Level</th>
                      <th scope="col">Proficiency Bonus</th>
                      <template v-if="allClasses[pageChanger].sorceryPoints == true">
                        <th scope="col">Sorcery Points</th>
                      </template>
                        <th scope="col">Features</th>
                      <template v-if="allClasses[pageChanger].hasMartialArts == true">
                        <th scope="col">Martial Arts</th>
                      </template>
                      <template v-if="allClasses[pageChanger].hasKiPoints == true">
                        <th scope="col">Ki Points</th>
                      </template>
                      <template v-if="allClasses[pageChanger].hasUnarmoredMovement == true">
                        <th scope="col">Unarmored Movement</th>
                      </template>
                      <template v-if="allClasses[pageChanger].hasSneakAttack == true">
                        <th scope="col">Sneak Attack</th>
                      </template>
                      <template v-if="allClasses[pageChanger].hasRages == true">
                        <th scope="col">Rages</th>
                      </template>
                      <template v-if="allClasses[pageChanger].hasRageDamage == true">
                        <th scope="col">Rage Damage</th>
                      </template>
                      <template v-if="allClasses[pageChanger].hasCantrips == true">
                        <th scope="col">Cantrips Known</th>
                      </template>
                      <template v-if="allClasses[pageChanger].spellsKnown == true">
                        <th scope="col">Spells Known</th>
                      </template>
                      <template v-if="allClasses[pageChanger].type == 'Spellcaster' || allClasses[pageChanger].type == 'halfSpellcaster'">
                          <th scope="col">1st</th>
                          <th scope="col">2nd</th>
                          <th scope="col">3rd</th>
                          <th scope="col">4th</th>
                          <th scope="col">5th</th>
                         <template v-if="allClasses[pageChanger].type == 'Spellcaster'">
                          <th scope="col">6th</th>
                          <th scope="col">7th</th>
                          <th scope="col">8th</th>
                          <th scope="col">9th</th>
                        </template>
                      </template>
                      <template v-if="allClasses[pageChanger].type == 'invocationSpellcaster'">
                          <th scope="col">Spell Slots</th>
                          <th scope="col">Slot Level</th>
                          <th scope="col">Invocations Known</th>
                      </template>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="item in allClasses[pageChanger].infoForEachLevel" v-bind:key="item.level">                         
                      <th scope="row">{{item.level}}</th>
                      <td>{{item.proficiencyBonus}}</td>
                      <template v-if="allClasses[pageChanger].sorceryPoints == true">
                        <td>{{item.sorceryPoints}}</td>
                      </template>
                      <td>{{item.feature}}</td>
                      <template v-if="allClasses[pageChanger].hasMartialArts == true">
                        <td>{{item.martialArts}}</td>
                      </template>
                      <template v-if="allClasses[pageChanger].hasKiPoints == true">
                        <td>{{item.kiPoints}}</td>
                      </template>
                      <template v-if="allClasses[pageChanger].hasUnarmoredMovement == true">
                        <td>{{item.unarmoredMovement}}</td>
                      </template>
                      <template v-if="allClasses[pageChanger].hasRages == true">
                        <td>{{item.rage}}</td>
                      </template>
                      <template v-if="allClasses[pageChanger].hasRageDamage == true">
                        <td>{{item.rageDamage}}</td>
                      </template>
                      <template v-if="allClasses[pageChanger].hasCantrips == true">
                        <td>{{item.cantrips}}</td>
                      </template>
                      <template v-if="allClasses[pageChanger].hasSneakAttack == true">
                        <td>{{item.sneakAttack}}</td>
                      </template>
                      <template v-if="allClasses[pageChanger].spellsKnown == true">
                        <td>{{item.knownSpells}}</td>
                      </template>
                      <template v-if="allClasses[pageChanger].type == 'invocationSpellcaster'">
                        <td>{{item.warlockSpellSlots}}</td>
                      </template>
                      <template v-if="allClasses[pageChanger].type == 'invocationSpellcaster'">
                        <td>{{item.warlockSlotLevel}}</td>
                      </template>
                      <template v-if="allClasses[pageChanger].type == 'invocationSpellcaster'">
                        <td>{{item.warlockInvocations}}</td>
                      </template>
                      <template v-if="allClasses[pageChanger].type == 'Spellcaster' || allClasses[pageChanger].type == 'halfSpellcaster'">
                        <td v-for="(slots, index) in item.spellSlots" v-bind:key="`slots-${index}`">{{slots}}</td> 
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
              </div>
              </div>  
            </div>
            <div class="col-3 classes-sidebar-recommendations">
                <h3 class="similar-classes">Similar Classes</h3>
                <h4 class="similar-classes-example">{{allClasses[pageChanger].similarClasses.firstName}}</h4>
                <h5 class="similar-classes-example-description"><strong>Similarities:</strong>{{allClasses[pageChanger].similarClasses.firstDescription}}</h5>
                <button v-on:click="chooseClass('Sorcerer')" type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">{{allClasses[pageChanger].similarClasses.firstName}}</button>
                <h4 class="similar-classes-example">{{allClasses[pageChanger].similarClasses.secondName}}</h4>
                <h5 class="similar-classes-example-description"><strong>Similarities:</strong>{{allClasses[pageChanger].similarClasses.secondDescription}}</h5>
                <button v-on:click="chooseClass('Bard')" type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">{{allClasses[pageChanger].similarClasses.secondName}}</button>
                <h3 class="suitable-races">Suitable Races</h3>
                <h4 class="suitable-races-example">{{allClasses[pageChanger].suitableRaces.firstName}}</h4>
                <h5 class="suitable-races-example-description"><strong>Race Bonuses:</strong>{{allClasses[pageChanger].suitableRaces.firstDescription}}</h5>
                <button type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">{{allClasses[pageChanger].suitableRaces.firstName}}</button>
                <h4 class="suitable-races-example">{{allClasses[pageChanger].suitableRaces.secondName}}</h4>
                <h5 class="suitable-races-example-description"><strong>Race Bonuses:</strong>{{allClasses[pageChanger].suitableRaces.secondDescription}}</h5>
                <button type="button" class="btn btn-primary recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">{{allClasses[pageChanger].suitableRaces.secondName}}</button>
            </div>
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
      allClasses: {
        'Fighter':{
          name: 'Fighter',
          type: 'nonSpellcaster',
          spellsKnown: false,
          sorceryPoints: false,
          hasCantrips: false,
          hasSneakAttack: false,
          hasRages: false,
          hasRageDamage: false,
          hasMartialArts: false,
          hasKiPoints: false,
          hasUnarmoredMovement: false,
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
          infoForEachLevel: [
            {
              level: 1,
              proficiencyBonus: '+2',
              feature: "Fighting Style, Second Wind",
            },
            {
              level: 2,
              proficiencyBonus: '+2',
              feature: "Action Surge (x1)",
            },
            {
              level: 3,
              proficiencyBonus: '+2',
              feature: 'Martial Archetype',
            },
            {
              level: 4,
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
            },
            {
              level: 5,
              proficiencyBonus: '+3',
              feature: "Extra Attack (x1)",
            },
            {
              level: 6,
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
            },
            {
              level: 7,
              proficiencyBonus: '+3',
              feature: 'Martial Archetype feature',
            },
            {
              level: 8,
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
            },
            {
              level: 9,
              proficiencyBonus: '+4',
              feature: 'Indomitable (x1)',
            },
            {
              level: 10,
              proficiencyBonus: '+4',
              feature: "Martial Archetype feature",
            },
            {
              level: 11,
              proficiencyBonus: '+4',
              feature: "Extra Attack (x2)", 
            },
            {
              level: 12,
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
            },
            {
              level: 13,
              proficiencyBonus: '+5',
              feature: 'Indomitable (x2)',
            },
            {
              level: 14,
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
            },
            {
              level: 15,
              proficiencyBonus: '+5',
              feature: 'Martial Archetype feature',
            },
            {
              level: 16,
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
            },
            {
              level: 17,
              proficiencyBonus: '+6',
              feature: "Action Surge (x2), Indomitable (x3)",
            },
            {
              level: 18,
              proficiencyBonus: '+6',
              feature: "Martial Archetype feature",
            },
            {
              level: 19,
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
            },
            {
              level: 20,
              proficiencyBonus: '+6',
              feature: "Extra Attack (x3)",
            }
          ],
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
          spellsKnown: false,
          sorceryPoints: false,
          hasCantrips: true,
          hasSneakAttack: false,
          hasRages: false,
          hasRageDamage: false,
          hasMartialArts: false,
          hasKiPoints: false,
          hasUnarmoredMovement: false,
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
          infoForEachLevel: [
            {
              level: 1,
              proficiencyBonus: '+2',
              feature: "Spellcasting, Arcane Recovery",
              cantrips: 3,
              spellSlots: [2, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 2,
              proficiencyBonus: '+2',
              feature: "Arcane Tradition",
              cantrips: 3,
              spellSlots: [3, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 3,
              proficiencyBonus: '+2',
              feature: '',
              cantrips: 3,
              spellSlots: [4, 2, '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 4,
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [4, 3, '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 5,
              proficiencyBonus: '+3',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 2, '-', '-', '-', '-', '-', '-']
            },
            {
              level: 6,
              proficiencyBonus: '+3',
              feature: "Arcane Tradition feature", 
              cantrips: 4,
              spellSlots: [4, 3, 3, '-', '-', '-', '-', '-', '-']
            },
            {
              level: 7,
              proficiencyBonus: '+3',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 1, '-', '-', '-', '-', '-']
            },
            {
              level: 8,
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [4, 3, 3, 2, '-', '-', '-', '-', '-']
            },
            {
              level: 9,
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 1, '-', '-', '-', '-']
            },
            {
              level: 10,
              proficiencyBonus: '+4',
              feature: "Arcane Tradition feature",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, '-', '-', '-', '-']
            },
            {
              level: 11,
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            {
              level: 12,
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            {
              level: 13,
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            {
              level: 14,
              proficiencyBonus: '+5',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            {
              level: 15,
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            {
              level: 16,
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement", 
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            {
              level: 17,
              proficiencyBonus: '+6',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, 1]
            },
            {
              level: 18,
              proficiencyBonus: '+6',
              feature: "Spell Mastery",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 3, 1, 1, 1, 1]
            },
            {
              level: 19,
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 3, 2, 1, 1, 1]
            },
            {
              level: 20,
              proficiencyBonus: '+6',
              feature: "Signature Spells",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 3, 2, 2, 1, 1]
            }
          ],
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
          spellsKnown: false,
          sorceryPoints: false,
          hasCantrips: false,
          hasSneakAttack: true,
          hasRages: false,
          hasRageDamage: false,
          hasMartialArts: false,
          hasKiPoints: false,
          hasUnarmoredMovement: false,
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
          infoForEachLevel: [
            {
              level: 1,
              proficiencyBonus: '+2',
              sneakAttack: '1d6',
              feature: "Expertise, Sneak Attack, Thieves' Cant",
            },
            {
              level: 2,
              proficiencyBonus: '+2',
              sneakAttack: '1d6',
              feature: "Cunning Action",
            },
            {
              level: 3,
              proficiencyBonus: '+2',
              sneakAttack: '2d6',
              feature: 'Roguish Archetype',
            },
            {
              level: 4,
              proficiencyBonus: '+2',
              sneakAttack: '2d6',
              feature: "Ability Score Improvement",
            },
            {
              level: 5,
              proficiencyBonus: '+3',
              sneakAttack: '3d6',
              feature: "Uncanny Dodge",
            },
            {
              level: 6,
              proficiencyBonus: '+3',
              sneakAttack: '3d6',
              feature: "Expertise",
            },
            {
              level: 7,
              proficiencyBonus: '+3',
              sneakAttack: '4d6',
              feature: 'Evasion',
            },
            {
              level: 8,
              proficiencyBonus: '+3',
              sneakAttack: '4d6',
              feature: "Ability Score Improvement",
            },
            {
              level: 9,
              proficiencyBonus: '+4',
              sneakAttack: '5d6',
              feature: 'Roguish Archetype feature',
            },
            {
              level: 10,
              proficiencyBonus: '+4',
              sneakAttack: '5d6',
              feature: "Ability Score Improvement",
            },
            {
              level: 11,
              proficiencyBonus: '+4',
              sneakAttack: '6d6',
              feature: "Reliable Talent", 
            },
            {
              level: 12,
              proficiencyBonus: '+4',
              sneakAttack: '6d6',
              feature: "Ability Score Improvement",
            },
            {
              level: 13,
              proficiencyBonus: '+5',
              sneakAttack: '7d6',
              feature: 'Roguish Archetype feature',
            },
            {
              level: 14,
              proficiencyBonus: '+5',
              sneakAttack: '7d6',
              feature: "Blindsense",
            },
            {
              level: 15,
              proficiencyBonus: '+5',
              sneakAttack: '8d6',
              feature: 'Slippery Mind',
            },
            {
              level: 16,
              proficiencyBonus: '+5',
              sneakAttack: '8d6',
              feature: "Ability Score Improvement",
            },
            {
              level: 17,
              proficiencyBonus: '+6',
              sneakAttack: '9d6',
              feature: "Roguish Archetype feature",
            },
            {
              level: 18,
              proficiencyBonus: '+6',
              sneakAttack: '9d6',
              feature: "Elusive",
            },
            {
              level: 19,
              proficiencyBonus: '+6',
              sneakAttack: '10d6',
              feature: "Ability Score Improvement",
            },
            {
              level: 20,
              proficiencyBonus: '+6',
              sneakAttack: '10d6',
              feature: "Stroke of Luck",
            }
          ],
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
          spellsKnown: false,
          sorceryPoints: false,
          hasCantrips: true,
          hasSneakAttack: false,
          hasRages: false,
          hasRageDamage: false,
          hasMartialArts: false,
          hasKiPoints: false,
          hasUnarmoredMovement: false,
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
          infoForEachLevel: [
            {
              level: 1,
              proficiencyBonus: '+2',
              feature: "Spellcasting, Divine Domain",
              cantrips: 3,
              spellSlots: [2, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 2,
              proficiencyBonus: '+2',
              feature: "Channel Divinity (x1), Divine Domain feature",
              cantrips: 3,
              spellSlots: [3, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 3,
              proficiencyBonus: '+2',
              feature: '',
              cantrips: 3,
              spellSlots: [4, 2, '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 4,
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [4, 3, '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 5,
              proficiencyBonus: '+3',
              feature: "Destroy Undead (CR 1/2)",
              cantrips: 4,
              spellSlots: [4, 3, 2, '-', '-', '-', '-', '-', '-']
            },
            {
              level: 6,
              proficiencyBonus: '+3',
              feature: "Channel Divinity (x2), Divine Domain feature",
              cantrips: 4,
              spellSlots: [4, 3, 3, '-', '-', '-', '-', '-', '-']
            },
            {
              level: 7,
              proficiencyBonus: '+3',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 1, '-', '-', '-', '-', '-']
            },
            {
              level: 8,
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement, Destroy Undead (CR 1), Divine Domain feature",
              cantrips: 4,
              spellSlots: [4, 3, 3, 2, '-', '-', '-', '-', '-']
            },
            {
              level: 9,
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 1, '-', '-', '-', '-']
            },
            {
              level: 10,
              proficiencyBonus: '+4',
              feature: "Divine Intervention",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, '-', '-', '-', '-']
            },
            {
              level: 11,
              proficiencyBonus: '+4',
              feature: "Destroy Undead (CR 2)", 
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            {
              level: 12,
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            {
              level: 13,
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            {
              level: 14,
              proficiencyBonus: '+5',
              feature: "Destroy Undead (CR 3)",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            {
              level: 15,
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            {
              level: 16,
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            {
              level: 17,
              proficiencyBonus: '+6',
              feature: "Destroy Undead (CR 4), Divine Domain feature",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, 1]
            },
            {
              level: 18,
              proficiencyBonus: '+6',
              feature: "Channel Divinity (x3)",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 3, 1, 1, 1, 1]
            },
            {
              level: 19,
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 3, 2, 1, 1, 1]
            },
            {
              level: 20,
              proficiencyBonus: '+6',
              feature: "Divine Intervention improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 3, 2, 2, 1, 1]
            }
          ],
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
          spellsKnown: false,
          sorceryPoints: false,
          hasCantrips: true,
          hasSneakAttack: false,
          hasRages: false,
          hasRageDamage: false,
          hasMartialArts: false,
          hasKiPoints: false,
          hasUnarmoredMovement: false,
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
          infoForEachLevel: [
            {
              level: 1,
              proficiencyBonus: '+2',
              feature: "Druidic, Spellcasting", 
              cantrips: 2,
              spellSlots: [2, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 2,
              proficiencyBonus: '+2',
              feature: "Wild Shape, Druid Circle", 
              cantrips: 2,
              spellSlots: [3, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 3,
              proficiencyBonus: '+2',
              feature: '',
              cantrips: 2,
              spellSlots: [4, 2, '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 4,
              proficiencyBonus: '+2',
              feature: "Wild Shape improvement, Ability Score Improvement", 
              cantrips: 3,
              spellSlots: [4, 3, '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 5,
              proficiencyBonus: '+3',
              feature: '',
              cantrips: 3,
              spellSlots: [4, 3, 2, '-', '-', '-', '-', '-', '-']
            },
            {
              level: 6,
              proficiencyBonus: '+3',              
              feature: "Druid Circle feature", 
              cantrips: 3,
              spellSlots: [4, 3, 3, '-', '-', '-', '-', '-', '-']
            },
            {
              level: 7,
              proficiencyBonus: '+3',
              feature: '',
              cantrips: 3,
              spellSlots: [4, 3, 3, 1, '-', '-', '-', '-', '-']
            },
            {
              level: 8,
              proficiencyBonus: '+3',
              feature: "Wild Shape improvement, Ability Score Improvement", 
              cantrips: 3,
              spellSlots: [4, 3, 3, 2, '-', '-', '-', '-', '-']
            },
            {
              level: 9,
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 3,
              spellSlots: [4, 3, 3, 3, 1, '-', '-', '-', '-']
            },
            {
              level: 10,
              proficiencyBonus: '+4',
              feature: "Druid Circle feature", 
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, '-', '-', '-', '-']
            },
            {
              level: 11,
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            {
              level: 12,
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            {
              level: 13,
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            {
              level: 14,
              proficiencyBonus: '+5',
              feature: "Druid Circle feature", 
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            {
              level: 15,
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            {
              level: 16,
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement", 
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            {
              level: 17,
              proficiencyBonus: '+6',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, 1]
            },
            {
              level: 18,
              proficiencyBonus: '+6',
              feature: "Timeless Body, Beast Spells",
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 3, 1, 1, 1, 1]
            },
            {
              level: 19,
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 3, 2, 1, 1, 1]
            },
            {
              level: 20,
              proficiencyBonus: '+6',
              feature: "Archdruid",
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 3, 2, 2, 1, 1]
            }
          ],
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
          spellsKnown: false,
          sorceryPoints: false,
          hasCantrips: false,
          hasSneakAttack: false,
          hasRages: false,
          hasRageDamage: false,
          hasMartialArts: true,
          hasKiPoints: true,
          hasUnarmoredMovement: true,
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
          infoForEachLevel: [
            {
              level: 1,
              proficiencyBonus: '+2',
              feature: "Unarmored Defense, Martial Arts",
              martialArts: '1d4',
              kiPoints: '-',
              unarmoredMovement: '-'
            },
            {
              level: 2,
              proficiencyBonus: '+2',
              feature: "Ki, Unarmored Movement",
              martialArts: '1d4',
              kiPoints: 2,
              unarmoredMovement: '+10ft'
            },
            {
              level: 3,
              proficiencyBonus: '+2',
              feature: 'Monastic Tradition, Deflect Missiles',
              martialArts: '1d4',
              kiPoints: 3,
              unarmoredMovement: '+10ft'
            },
            {
              level: 4,
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement, Slow Fall",
              martialArts: '1d4',
              kiPoints: 4,
              unarmoredMovement: '+10ft'
            },
            {
              level: 5,
              proficiencyBonus: '+3',
              feature: "Extra Attack, Stunning Strike",
              martialArts: '1d6',
              kiPoints: 5,
              unarmoredMovement: '+10ft'
            },
            {
              level: 6,
              proficiencyBonus: '+3',
              feature: "Ki-Empowered Strikes, Monastic Tradition feature",
              martialArts: '1d6',
              kiPoints: 6,
              unarmoredMovement: '+15ft'
            },
            {
              level: 7,
              proficiencyBonus: '+3',
              feature: 'Evasion, Stillness of Mind',
              martialArts: '1d6',
              kiPoints: 7,
              unarmoredMovement: '+15ft'
            },
            {
              level: 8,
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
              martialArts: '1d6',
              kiPoints: 8,
              unarmoredMovement: '+15ft'
            },
            {
              level: 9,
              proficiencyBonus: '+4',
              feature: 'Unarmored Movement improvement',
              martialArts: '1d6',
              kiPoints: 9,
              unarmoredMovement: '+15ft'
            },
            {
              level: 10,
              proficiencyBonus: '+4',
              feature: "Purity of Body",
              martialArts: '1d6',
              kiPoints: 10,
              unarmoredMovement: '+20ft'
            },
            {
              level: 11,
              proficiencyBonus: '+4',
              feature: "Monastic Tradition feature", 
              martialArts: '1d8',
              kiPoints: 11,
              unarmoredMovement: '+20ft'
            },
            {
              level: 12,
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              martialArts: '1d8',
              kiPoints: 12,
              unarmoredMovement: '+20ft'
            },
            {
              level: 13,
              proficiencyBonus: '+5',
              feature: 'Tongue of the Sun and Moon',
              martialArts: '1d8',
              kiPoints: 13,
              unarmoredMovement: '+20ft'
            },
            {
              level: 14,
              proficiencyBonus: '+5',
              feature: "Diamond Soul",
              martialArts: '1d8',
              kiPoints: 14,
              unarmoredMovement: '+25ft'
            },
            {
              level: 15,
              proficiencyBonus: '+5',
              feature: 'Timeless Body',
              martialArts: '1d8',
              kiPoints: 15,
              unarmoredMovement: '+25ft'
            },
            {
              level: 16,
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
              martialArts: '1d8',
              kiPoints: 16,
              unarmoredMovement: '+25ft'
            },
            {
              level: 17,
              proficiencyBonus: '+6',
              feature: "Monastic Tradition feature",
              martialArts: '1d10',
              kiPoints: 17,
              unarmoredMovement: '+25ft'
            },
            {
              level: 18,
              proficiencyBonus: '+6',
              feature: "Empty Body",
              martialArts: '1d10',
              kiPoints: 18,
              unarmoredMovement: '+30ft'
            },
            {
              level: 19,
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              martialArts: '1d10',
              kiPoints: 19,
              unarmoredMovement: '+30ft'
            },
            {
              level: 20,
              proficiencyBonus: '+6',
              feature: "Perfect Self",
              martialArts: '1d10',
              kiPoints: 20,
              unarmoredMovement: '+30ft'
            }
          ],       
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
          spellsKnown: false,
          sorceryPoints: false,
          hasCantrips: false,
          hasSneakAttack: false,
          hasRages: false,
          hasRageDamage: false,
          hasMartialArts: false,
          hasKiPoints: false,
          hasUnarmoredMovement: false,
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
          infoForEachLevel: [
            {
              level: 1,
              proficiencyBonus: '+2',
              feature: "Divine Sense, Lay on Hands",
              cantrips: 3,
              spellSlots: ['-', '-', '-', '-', '-']
            },
            {
              level: 2,
              proficiencyBonus: '+2',
              feature: "Fighting Style, Spellcasting, Divine Smite",
              cantrips: 3,
              spellSlots: [2, '-', '-', '-', '-']
            },
            {
              level: 3,
              proficiencyBonus: '+2',
              feature: 'Divine Health, Sacred Oath',
              cantrips: 3,
              spellSlots: [3, '-', '-', '-', '-']
            },
            {
              level: 4,
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [3, '-', '-', '-', '-']
            },
            {
              level: 5,
              proficiencyBonus: '+3',
              feature: "Extra Attack",
              cantrips: 4,
              spellSlots: [4, 2, '-', '-', '-']
            },
            {
              level: 6,
              proficiencyBonus: '+3',
              feature: "Aura of Protection",
              cantrips: 4,
              spellSlots: [4, 2, '-', '-', '-']
            },
            {
              level: 7,
              proficiencyBonus: '+3',
              feature: 'Sacred Oath feature',
              cantrips: 4,
              spellSlots: [4, 3, '-', '-', '-']
            },
            {
              level: 8,
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
              cantrips: 4,
              spellSlots: [4, 3, '-', '-', '-']
            },
            {
              level: 9,
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 4,
              spellSlots: [4, 3, 2, '-', '-']
            },
            {
              level: 10,
              proficiencyBonus: '+4',
              feature: "Aura of Courage",
              cantrips: 5,
              spellSlots: [4, 3, 2, '-', '-']
            },
            {
              level: 11,
              proficiencyBonus: '+4',
              feature: "Improved Divine Smite", 
              cantrips: 5,
              spellSlots: [4, 3, 3, '-', '-']
            },
            {
              level: 12,
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, '-', '-']
            },
            {
              level: 13,
              proficiencyBonus: '+5',
              feature: '',
              cantrips: 5,
              spellSlots: [4, 3, 3, 1, '-']
            },
            {
              level: 14,
              proficiencyBonus: '+5',
              feature: "Cleansing Touch",
              cantrips: 5,
              spellSlots: [4, 3, 3, 1, '-']
            },
            {
              level: 15,
              proficiencyBonus: '+5',
              feature: 'Sacred Oath feature',
              cantrips: 5,
              spellSlots: [4, 3, 3, 2, '-']
            },
            {
              level: 16,
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 2, '-']
            },
            {
              level: 17,
              proficiencyBonus: '+6',
              feature: "",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 1]
            },
            {
              level: 18,
              proficiencyBonus: '+6',
              feature: "Aura improvements",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 1]
            },
            {
              level: 19,
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2]
            },
            {
              level: 20,
              proficiencyBonus: '+6',
              feature: "Sacred Oath feature",
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 2]
            }
          ],
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
          spellsKnown: true,
          sorceryPoints: false,
          hasCantrips: false,
          hasSneakAttack: false,
          hasRages: false,
          hasRageDamage: false,
          hasMartialArts: false,
          hasKiPoints: false,
          hasUnarmoredMovement: false,
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
          infoForEachLevel: [
            {
              level: 1,
              proficiencyBonus: '+2',
              feature: "Favored Enemy, Natural Explorer",
              knownSpells: '-',
              spellSlots: ['-', '-', '-', '-', '-']
            },
            {
              level: 2,
              proficiencyBonus: '+2',
              feature: "Fighting Style, Spellcasting",
              knownSpells: '2',
              spellSlots: [2, '-', '-', '-', '-']
            },
            {
              level: 3,
              proficiencyBonus: '+2',
              feature: 'Primeval Awareness, Ranger Conclave',
              knownSpells: '3',
              spellSlots: [3, '-', '-', '-', '-']
            },
            {
              level: 4,
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              knownSpells: '3',
              spellSlots: [3, '-', '-', '-', '-']
            },
            {
              level: 5,
              proficiencyBonus: '+3',
              feature: "Ranger Conclave feature",
              knownSpells: '4',
              spellSlots: [4, 2, '-', '-', '-']
            },
            {
              level: 6,
              proficiencyBonus: '+3',
              feature: "Greater Favored Enemy",
              knownSpells: '4',
              spellSlots: [4, 2, '-', '-', '-']
            },
            {
              level: 7,
              proficiencyBonus: '+3',
              feature: 'Ranger Conclave feature',
              knownSpells: '5',
              spellSlots: [4, 3, '-', '-', '-']
            },
            {
              level: 8,
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement, Fleet of Foot",
              knownSpells: '5',
              spellSlots: [4, 3, '-', '-', '-']
            },
            {
              level: 9,
              proficiencyBonus: '+4',
              feature: '',
              knownSpells: '6',
              spellSlots: [4, 3, 2, '-', '-']
            },
            {
              level: 10,
              proficiencyBonus: '+4',
              feature: "Hide in Plain Sight",
              knownSpells: '6',
              spellSlots: [4, 3, 2, '-', '-']
            },
            {
              level: 11,
              proficiencyBonus: '+4',
              feature: "Ranger Conclave feature", 
              knownSpells: '7',
              spellSlots: [4, 3, 3, '-', '-']
            },
            {
              level: 12,
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              knownSpells: '7',
              spellSlots: [4, 3, 3, '-', '-']
            },
            {
              level: 13,
              proficiencyBonus: '+5',
              feature: '',
              knownSpells: '8',
              spellSlots: [4, 3, 3, 1, '-']
            },
            {
              level: 14,
              proficiencyBonus: '+5',
              feature: "Vanish",
              knownSpells: '8',
              spellSlots: [4, 3, 3, 1, '-']
            },
            {
              level: 15,
              proficiencyBonus: '+5',
              feature: 'Ranger Conclave feature',
              knownSpells: '9',
              spellSlots: [4, 3, 3, 2, '-']
            },
            {
              level: 16,
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
              knownSpells: '9',
              spellSlots: [4, 3, 3, 2, '-']
            },
            {
              level: 17,
              proficiencyBonus: '+6',
              feature: "",
              knownSpells: '10',
              spellSlots: [4, 3, 3, 3, 1]
            },
            {
              level: 18,
              proficiencyBonus: '+6',
              feature: "Feral Senses",
              knownSpells: '10',
              spellSlots: [4, 3, 3, 3, 1]
            },
            {
              level: 19,
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              knownSpells: '11',
              spellSlots: [4, 3, 3, 3, 2]
            },
            {
              level: 20,
              proficiencyBonus: '+6',
              feature: "Foe Slayer",
              knownSpells: '11',
              spellSlots: [4, 3, 3, 3, 2]
            }
          ],
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
          spellsKnown: true,
          sorceryPoints: true,
          hasCantrips: true,
          hasSneakAttack: false,
          hasRages: false,
          hasRageDamage: false,
          hasMartialArts: false,
          hasKiPoints: false,
          hasUnarmoredMovement: false,
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
          infoForEachLevel: [
            {
              level: 1,
              proficiencyBonus: '+2',
              feature: "Spellcasting, Sorcerous Origin",
              knownSpells: 2,
              sorceryPoints: '-',
              cantrips: 4,
              spellSlots: [2, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 2,
              proficiencyBonus: '+2',
              feature: "Font of Magic",
              knownSpells: 3,
              sorceryPoints: 2,
              cantrips: 4,
              spellSlots: [3, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 3,
              proficiencyBonus: '+2',
              feature: 'Metamagic',
              knownSpells: 4,
              sorceryPoints: 3,
              cantrips: 4,
              spellSlots: [4, 2, '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 4,
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              knownSpells: 5,
              sorceryPoints: 4,
              cantrips: 5,
              spellSlots: [4, 3, '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 5,
              proficiencyBonus: '+3',
              feature: '',
              knownSpells: 6,
              sorceryPoints: 5,
              cantrips: 5,
              spellSlots: [4, 3, 2, '-', '-', '-', '-', '-', '-']
            },
            {
              level: 6,
              proficiencyBonus: '+3',
              feature: "Sorcerous Origin feature", 
              knownSpells: 7,
              sorceryPoints: 6,
              cantrips: 5,
              spellSlots: [4, 3, 3, '-', '-', '-', '-', '-', '-']
            },
            {
              level: 7,
              proficiencyBonus: '+3',
              feature: '',
              knownSpells: 8,
              sorceryPoints: 7,
              cantrips: 5,
              spellSlots: [4, 3, 3, 1, '-', '-', '-', '-', '-']
            },
            {
              level: 8,
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
              knownSpells: 9,
              sorceryPoints: 8,
              cantrips: 5,
              spellSlots: [4, 3, 3, 2, '-', '-', '-', '-', '-']
            },
            {
              level: 9,
              proficiencyBonus: '+4',
              feature: '',
              knownSpells: 10,
              sorceryPoints: 9,
              cantrips: 5,
              spellSlots: [4, 3, 3, 3, 1, '-', '-', '-', '-']
            },
            {
              level: 10,
              proficiencyBonus: '+4',
              feature: "Metamagic",
              knownSpells: 11,
              sorceryPoints: 10,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, '-', '-', '-', '-']
            },
            {
              level: 11,
              proficiencyBonus: '+4',
              feature: '',
              knownSpells: 12,
              sorceryPoints: 11,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            {
              level: 12,
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              knownSpells: 12,
              sorceryPoints: 12,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            {
              level: 13,
              proficiencyBonus: '+5',
              feature: '',
              knownSpells: 13,
              sorceryPoints: 13,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            {
              level: 14,
              proficiencyBonus: '+5',
              feature: 'Sorcerous Origin feature',
              knownSpells: 13,
              sorceryPoints: 14,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            {
              level: 15,
              proficiencyBonus: '+5',
              feature: '',
              knownSpells: 14,
              sorceryPoints: 15,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            {
              level: 16,
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement", 
              knownSpells: 14,
              sorceryPoints: 16,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            {
              level: 17,
              proficiencyBonus: '+6',
              feature: 'Metamagic',
              knownSpells: 15,
              sorceryPoints: 17,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, 1]
            },
            {
              level: 18,
              proficiencyBonus: '+6',
              feature: "Sorcerous Origin feature",
              knownSpells: 15,
              sorceryPoints: 18,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 3, 1, 1, 1, 1]
            },
            {
              level: 19,
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              knownSpells: 15,
              sorceryPoints: 19,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 3, 2, 1, 1, 1]
            },
            {
              level: 20,
              proficiencyBonus: '+6',
              feature: "Sorcerous Restoration",
              knownSpells: 15,
              sorceryPoints: 20,
              cantrips: 6,
              spellSlots: [4, 3, 3, 3, 3, 2, 2, 1, 1]
            }
          ],
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
          spellsKnown: true,
          sorceryPoints: false,
          hasCantrips: true,
          hasSneakAttack: false,
          hasRages: false,
          hasRageDamage: false,
          hasMartialArts: false,
          hasKiPoints: false,
          hasUnarmoredMovement: false,
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
          infoForEachLevel: [
            {
              level: 1,
              proficiencyBonus: '+2',
              feature: "Otherworldly Patron, Pact Magic",
              cantrips: 2,
              knownSpells: 2,
              warlockSpellSlots: 1,
              warlockSlotLevel: '1st',
              warlockInvocations: '-'
            },
            {
              level: 2,
              proficiencyBonus: '+2',
              feature: "Eldritch Invocations",
              cantrips: 2,
              knownSpells: 3,
              warlockSpellSlots: 2,
              warlockSlotLevel: '1st',
              warlockInvocations: '2'
            },
            {
              level: 3,
              proficiencyBonus: '+2',
              feature: 'Pact Boon',
              cantrips: 2,
              knownSpells: 4,
              warlockSpellSlots: 2,
              warlockSlotLevel: '2nd',
              warlockInvocations: '2'
            },
            {
              level: 4,
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              cantrips: 3,
              knownSpells: 5,
              warlockSpellSlots: 2,
              warlockSlotLevel: '2nd',
              warlockInvocations: '2'
            },
            {
              level: 5,
              proficiencyBonus: '+3',
              feature: "",
              cantrips: 3,
              knownSpells: 6,
              warlockSpellSlots: 2,
              warlockSlotLevel: '3rd',
              warlockInvocations: '3'
            },
            {
              level: 6,
              proficiencyBonus: '+3',
              feature: "Otherworldly Patron feature",
              cantrips: 3,
              knownSpells: 7,
              warlockSpellSlots: 2,
              warlockSlotLevel: '3rd',
              warlockInvocations: '3'
            },
            {
              level: 7,
              proficiencyBonus: '+3',
              feature: '',
              cantrips: 3,
              knownSpells: 8,
              warlockSpellSlots: 2,
              warlockSlotLevel: '4th',
              warlockInvocations: '4'
            },
            {
              level: 8,
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
              cantrips: 3,
              knownSpells: 9,
              warlockSpellSlots: 2,
              warlockSlotLevel: '4th',
              warlockInvocations: '4'
            },
            {
              level: 9,
              proficiencyBonus: '+4',
              feature: '',
              cantrips: 3,
              knownSpells: 10,
              warlockSpellSlots: 2,
              warlockSlotLevel: '5th',
              warlockInvocations: '5'
            },
            {
              level: 10,
              proficiencyBonus: '+4',
              feature: "Otherworldly Patron feature",
              cantrips: 4,
              knownSpells: 10,
              warlockSpellSlots: 2,
              warlockSlotLevel: '5th',
              warlockInvocations: '5'
            },
            {
              level: 11,
              proficiencyBonus: '+4',
              feature: "Mystic Arcanum (6th level)",
              cantrips: 4, 
              knownSpells: 11,
              warlockSpellSlots: 3,
              warlockSlotLevel: '5th',
              warlockInvocations: '5'
            },
            {
              level: 12,
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              cantrips: 4,
              knownSpells: 11,
              warlockSpellSlots: 3,
              warlockSlotLevel: '5th',
              warlockInvocations: '6'
            },
            {
              level: 13,
              proficiencyBonus: '+5',
              feature: 'Mystic Arcanum (7th level)',
              cantrips: 4,
              knownSpells: 12,
              warlockSpellSlots: 3,
              warlockSlotLevel: '5th',
              warlockInvocations: '6'
            },
            {
              level: 14,
              proficiencyBonus: '+5',
              feature: "Otherworldly Patron feature",
              cantrips: 4,
              knownSpells: 12,
              warlockSpellSlots: 3,
              warlockSlotLevel: '5th',
              warlockInvocations: '6'
            },
            {
              level: 15,
              proficiencyBonus: '+5',
              feature: 'Mystic Arcanum (8th level)',
              cantrips: 4,
              knownSpells: 13,
              warlockSpellSlots: 3,
              warlockSlotLevel: '5th',
              warlockInvocations: '7'
            },
            {
              level: 16,
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement",
              cantrips: 4,
              knownSpells: 13,
              warlockSpellSlots: 3,
              warlockSlotLevel: '5th',
              warlockInvocations: '7'
            },
            {
              level: 17,
              proficiencyBonus: '+6',
              feature: "Mystic Arcanum (9th level)",
              cantrips: 4,
              knownSpells: 14,
              warlockSpellSlots: 4,
              warlockSlotLevel: '5th',
              warlockInvocations: '7'
            },
            {
              level: 18,
              proficiencyBonus: '+6',
              feature: "",
              cantrips: 4,
              knownSpells: 14,
              warlockSpellSlots: 4,
              warlockSlotLevel: '5th',
              warlockInvocations: '8'
            },
            {
              level: 19,
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              cantrips: 4,
              knownSpells: 15,
              warlockSpellSlots: 4,
              warlockSlotLevel: '5th',
              warlockInvocations: '8'
            },
            {
              level: 20,
              proficiencyBonus: '+6',
              feature: "Eldritch Master",
              cantrips: 4,
              knownSpells: 15,
              warlockSpellSlots: 4,
              warlockSlotLevel: '5th',
              warlockInvocations: '8'
            }
          ],
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
          spellsKnown: true,
          sorceryPoints: false,
          hasCantrips: true,
          hasSneakAttack: false,
          hasRages: false,
          hasRageDamage: false,
          hasMartialArts: false,
          hasKiPoints: false,
          hasUnarmoredMovement: false,
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
          infoForEachLevel: [
            {
              level: 1,
              proficiencyBonus: '+2',
              feature: "Spellcasting, Bardic Inspiration (d6)",
              knownSpells: 4,
              cantrips: 2,
              spellSlots: [2, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 2,
              proficiencyBonus: '+2',
              feature: "Jack of All Trades, Song of Rest (d6)",
              knownSpells: 5,
              cantrips: 2,
              spellSlots: [3, '-', '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 3,
              proficiencyBonus: '+2',
              feature: 'Bard College, Expertise',
              knownSpells: 6,
              cantrips: 2,
              spellSlots: [4, 2, '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 4,
              proficiencyBonus: '+2',
              feature: "Ability Score Improvement",
              knownSpells: 7,
              cantrips: 3,
              spellSlots: [4, 3, '-', '-', '-', '-', '-', '-', '-']
            },
            {
              level: 5,
              proficiencyBonus: '+3',
              feature: 'Bardic Inspiration (d8), Font of Inspiration',
              knownSpells: 8,
              cantrips: 3,
              spellSlots: [4, 3, 2, '-', '-', '-', '-', '-', '-']
            },
            {
              level: 6,
              proficiencyBonus: '+3',
              feature: "Countercharm, Bard College feature", 
              knownSpells: 9,
              cantrips: 3,
              spellSlots: [4, 3, 3, '-', '-', '-', '-', '-', '-']
            },
            {
              level: 7,
              proficiencyBonus: '+3',
              feature: '',
              knownSpells: 10,
              cantrips: 3,
              spellSlots: [4, 3, 3, 1, '-', '-', '-', '-', '-']
            },
            {
              level: 8,
              proficiencyBonus: '+3',
              feature: "Ability Score Improvement",
              knownSpells: 11,
              cantrips: 3,
              spellSlots: [4, 3, 3, 2, '-', '-', '-', '-', '-']
            },
            {
              level: 9,
              proficiencyBonus: '+4',
              feature: 'Song of Rest (d8)',
              knownSpells: 12,
              cantrips: 3,
              spellSlots: [4, 3, 3, 3, 1, '-', '-', '-', '-']
            },
            {
              level: 10,
              proficiencyBonus: '+4',
              feature: "Bardic Inspiration (d10), Expertise, Magical Secrets",
              knownSpells: 14,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, '-', '-', '-', '-']
            },
            {
              level: 11,
              proficiencyBonus: '+4',
              feature: '',
              knownSpells: 15,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            {
              level: 12,
              proficiencyBonus: '+4',
              feature: "Ability Score Improvement",
              knownSpells: 15,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, '-', '-', '-']
            },
            {
              level: 13,
              proficiencyBonus: '+5',
              feature: 'Song of Rest (d10)',
              knownSpells: 16,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            {
              level: 14,
              proficiencyBonus: '+5',
              feature: 'Magical Secrets, Bard College feature',
              knownSpells: 18,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, '-', '-']
            },
            {
              level: 15,
              proficiencyBonus: '+5',
              feature: 'Bardic Inspiration (d12)',
              knownSpells: 19,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            {
              level: 16,
              proficiencyBonus: '+5',
              feature: "Ability Score Improvement", 
              knownSpells: 19,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, '-']
            },
            {
              level: 17,
              proficiencyBonus: '+6',
              feature: 'Song of Rest (d12)',
              knownSpells: 20,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 2, 1, 1, 1, 1]
            },
            {
              level: 18,
              proficiencyBonus: '+6',
              feature: "Magical Secrets",
              knownSpells: 22,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 3, 1, 1, 1, 1]
            },
            {
              level: 19,
              proficiencyBonus: '+6',
              feature: "Ability Score Improvement",
              knownSpells: 22,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 3, 2, 1, 1, 1]
            },
            {
              level: 20,
              proficiencyBonus: '+6',
              feature: "Superior Inspiration",
              knownSpells: 22,
              cantrips: 4,
              spellSlots: [4, 3, 3, 3, 3, 2, 2, 1, 1]
            }
          ],
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
          spellsKnown: false,
          sorceryPoints: false,
          hasCantrips: false,
          hasSneakAttack: false,
          hasRages: true,
          hasRageDamage: true,
          hasMartialArts: false,
          hasKiPoints: false,
          hasUnarmoredMovement: false,
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
          infoForEachLevel: [
            {
              level: 1,
              proficiencyBonus: '+2',
              rage: 2,
              rageDamage: '+2',
              feature: "Rage, Unarmored Defense",
            },
            {
              level: 2,
              proficiencyBonus: '+2',
              rage: 2,
              rageDamage: '+2',
              feature: "Reckless Attack, Danger Sense",
            },
            {
              level: 3,
              proficiencyBonus: '+2',
              rage: 3,
              rageDamage: '+2',
              feature: 'Primal Path',
            },
            {
              level: 4,
              proficiencyBonus: '+2',
              rage: 3,
              rageDamage: '+2',
              feature: "Ability Score Improvement",
            },
            {
              level: 5,
              proficiencyBonus: '+3',
              rage: 3,
              rageDamage: '+2',
              feature: "Extra Attack, Fast Movement",
            },
            {
              level: 6,
              proficiencyBonus: '+3',
              rage: 4,
              rageDamage: '+2',
              feature: "Path feature",
            },
            {
              level: 7,
              proficiencyBonus: '+3',
              rage: 4,
              rageDamage: '+2',
              feature: 'Feral Instinct',
            },
            {
              level: 8,
              proficiencyBonus: '+3',
              rage: 4,
              rageDamage: '+2',
              feature: "Ability Score Improvement",
            },
            {
              level: 9,
              proficiencyBonus: '+4',
              rage: 4,
              rageDamage: '+3',
              feature: 'Brutal Critical (1 die)',
            },
            {
              level: 10,
              proficiencyBonus: '+4',
              rage: 4,
              rageDamage: '+3',
              feature: "Path feature",
            },
            {
              level: 11,
              proficiencyBonus: '+4',
              rage: 4,
              rageDamage: '+3',
              feature: "Relentless Rage", 
            },
            {
              level: 12,
              proficiencyBonus: '+4',
              rage: 5,
              rageDamage: '+3',
              feature: "Ability Score Improvement",
            },
            {
              level: 13,
              proficiencyBonus: '+5',
              rage: 5,
              rageDamage: '+3',
              feature: 'Brutal Critical (2 dice)',
            },
            {
              level: 14,
              proficiencyBonus: '+5',
              rage: 5,
              rageDamage: '+3',
              feature: "Path feature",
            },
            {
              level: 15,
              proficiencyBonus: '+5',
              rage: 5,
              rageDamage: '+3',
              feature: 'Persistent Rage',
            },
            {
              level: 16,
              proficiencyBonus: '+5',
              rage: 5,
              rageDamage: '+4',
              feature: "Ability Score Improvement",
            },
            {
              level: 17,
              proficiencyBonus: '+6',
              rage: 6,
              rageDamage: '+4',
              feature: "Brutal Critical (3 dice)",
            },
            {
              level: 18,
              proficiencyBonus: '+6',
              rage: 6,
              rageDamage: '+4',
              feature: "Indomitable Might",
            },
            {
              level: 19,
              proficiencyBonus: '+6',
              rage: 6,
              rageDamage: '+4',
              feature: "Ability Score Improvement",
            },
            {
              level: 20,
              proficiencyBonus: '+6',
              rage: 'Unlimited',
              rageDamage: '+4',
              feature: "Primal Champion",
            }
          ],
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
        'dragonborn':{
          name: 'Dragonborn',
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
            firstDescription: ' +2 Strength',
            secondName: 'Bard',
            secondDescription: ' +1 Charisma',
          },
        },
        'dwarf':{
          name: 'Dwarf',
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
        'elf':{},
        'gnome':{},
        'half-elf':{},
        'half-orc':{},
        'halfling':{},
        'human':{},
        'tiefling':{}
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
  color: #989a9c;
  font-weight: bold;
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
}
.classes-sidebar-recommendations{
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
.class-title-on-class-page{
   color: #151515;
   font-weight: bold;
}
.class-detailed-description{
  text-align: left;
}
.class-table{
  height: 75%;
}
.class-detailed-description-title{
  color: #000;
  padding-bottom: 30px;
}
.class-detailed-description-mini-title{
  color: #000;
  font-weight: bold;
}
.class-mini-description-on-class-page{
   text-align: left;
   font-weight: bold;
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
.similar-classes, .suitable-races{
  padding-bottom: 7px;
  padding-top: 50px;
  color: #151515;
  font-weight: bold;
}
.similar-classes-example, .suitable-races-example{
  padding-top: 20px;
  color: #15191d;
  font-weight: bold;
}
.suitable-races-example-description, .similar-classes-example-description{
  color: #15191d;
}
.classes-main-description{
  padding-right: 30px;
  padding-top: 40px;
}
.class-detailed-description{
  padding-top: 30px;
  padding-bottom: 50px;
}
</style>
