<template>
    <div class="calc">
        <div v-if="finalRace === 'Half-Elf' && checkRacialBonusesAmount()" class="row">
                <div class="container">
                    <div class="row hal-elf-buttons-row">
                        <h4>To play as a Half-Elf you need to choose two additional Racial Bonuses:</h4>
                    </div>
                    <div class="row hal-elf-buttons-row">
                        <button v-on:click="addToHalfElfRacialBonuses('Strength')" type="button" class="btn btn-primary half-elf-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                        Strength
                        </button>
                        <button v-on:click="addToHalfElfRacialBonuses('Dexterity')" type="button" class="btn btn-primary half-elf-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                        Dexterity
                        </button>
                        <button v-on:click="addToHalfElfRacialBonuses('Constitution')" type="button" class="btn btn-primary half-elf-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                        Constitution
                        </button>
                        <button v-on:click="addToHalfElfRacialBonuses('Intelligence')" type="button" class="btn btn-primary half-elf-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                        Intelligence
                        </button>
                        <button v-on:click="addToHalfElfRacialBonuses('Wisdom')" type="button" class="btn btn-primary half-elf-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                        Wisdom
                        </button>  
                    </div>
                </div>  
        </div>
        <div class="row calc-labels">
          <div class="container">
            <div class="row point-system-info">
                <h4>
                    <br>
                    All ability scores start at 8. You are allotted a number of 27 points to "buy" higher ability scores. To increase an ability score of 12 (or lower) to a higher one, you buy an increase on a 1-for-1 basis. The cost to increase your ability score from 13 to 14 or from 14 to 15 would be higher - 2 points. Before adding the racial bonus to the total score, you can have a maximum of 15 on each ability score. <br>
                    <br>
                    Ability Modifiers start as low as -1 for a Total Score of 8 and increase with 1 for every increase of the Total Score with 2. 
                </h4>
            </div>
            <div class="row tables-holder">
                <table class="table table-dark point-table">
                    <thead>
                        <tr>
                        <th scope="col">Ability Score</th>
                        <th scope="col">Point Cost</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <th scope="row">8</th>
                            <td>0</td>
                        </tr>
                        <tr>
                            <th scope="row">9</th>
                            <td>1 (+1 from previous)</td>
                        </tr>
                        <tr>
                            <th scope="row">10</th>
                            <td>2 (+1 from previous)</td>
                        </tr>
                        <tr>
                            <th scope="row">11</th>
                            <td>3 (+1 from previous)</td>
                        </tr>
                    </tbody>
                </table>
                <table class="table table-dark point-table">
                    <thead>
                        <tr>
                        <th scope="col">Ability Score</th>
                        <th scope="col">Point Cost</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <th scope="row">12</th>
                            <td>4 (+1 from previous)</td>
                        </tr>
                        <tr>
                            <th scope="row">13</th>
                            <td>5 (+1 from previous)</td>
                        </tr>
                        <tr>
                            <th scope="row">14</th>
                            <td style="font-weight: bold; color: salmon;">7 (+2 from previous)</td>
                        </tr>
                        <tr>
                            <th scope="row">15</th>
                            <td style="font-weight: bold; color: salmon;">9 (+2 from previous)</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div class="row calc-header">
              <div class="col-2">
                <p>Attribute</p>
              </div>
              <div class="col-2">
                <p>Ability Score</p>
              </div>
              <div class="col-1">
              </div>
              <div class="col-2">
                <p>Racial Bonus</p>
              </div>
              <div class="col-1">
              </div>
              <div class="col-2">
                <p>Total Score</p>
              </div>
              <div class="col-1">
                <p>Ability Modifier</p>
              </div>
              <div class="col-1">
                <p>Point Cost</p>
              </div>
            </div>
            <div v-for="(attribute, index) in attributes"  v-bind:key="index" class="row">
                <div class="col-2">
                    <p>{{attribute}}</p>
                </div>
                <div class="col-2">
                <div class="row">
                    <div class="col-9">
                        <p>{{attributesScores[attribute]}}</p>
                    </div>
                    <div class="col-3">
                    <div class="row">
                        <template v-if="pointsLeft > 0">
                            <button v-on:click="(attributesScores[attribute] < 15) ? increasePointScore(attributesScores[attribute], attribute) : attributesScores[attribute]" type="button" class="btn btn-primary btn-lg recommendations ability-score-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                            +
                            </button>
                        </template>
                    </div>
                    <div class="row">
                        <template>
                            <button v-on:click="(attributesScores[attribute] > 8) ? decreasePointScore(attributesScores[attribute], attribute) : attributesScores[attribute]" type="button" class="btn btn-primary btn-lg recommendations ability-score-btn" data-toggle="button" aria-pressed="false" autocomplete="off">
                            -
                            </button>
                        </template>
                    </div>
                    </div>
                </div>
                </div>
                <div class="col-1"> 
                    <p> + </p>
                </div>
                <div class="col-2">
                    <p>{{getRaceBonus(attribute, finalRace)}}</p>
                </div>
                <div class="col-1">
                    <p> = </p>
                </div>
                <div class="col-2">
                    <p>{{getTotalScore(getRaceBonus(attribute, finalRace), attributesScores[attribute], attribute)}}</p>
                </div>
                <div class="col-1">
                    <p>{{getModifier(attributesTotalScores[attribute], attribute)}}</p>
                </div>
                <div class="col-1">
                    <p>{{attributesPointScores[attribute]}}</p>
                </div>
            </div>
          </div>
        </div>
        <div class="row">
            <div class="container">
                <div class="row row-left-points">
                    <p>Points Left: {{pointsLeft}}</p>
                </div>
            </div>
        </div>
        <div class="row">
            <div class="container">
                <div class="row  final-row-calc">
                    <div class="char-name-form">
                            <label class="character-name-label" for="fname">Character Name:</label>
                            <input type="text" v-model="characterName" id="fname" name="firstname" placeholder="Your name..">
                    </div>
                    <div class="finish-btn-div">
                        <button v-on:click="openFinalSheet()" type="button" class="btn btn-primary btn-lg recommendations" data-toggle="button" aria-pressed="false" autocomplete="off">
                            Finish Character Creation
                        </button>
                    </div>
                </div>
            </div>
        </div>
       </div>
</template>
<script>
export default {
    name: 'AbilityCalculator',
    props: {
        calculatorRaces: Object,
        calculatorClasses: Object, 
        calculatorFinalClass: String,
        calculatorFinalRace: String,
        calculatorCharacterName: String,
        calculatorAttributesModifiers: Object,
        calculatorAttributesTotalScores: Object,
        calculatorPageChanger: String

    },
    data () {
        return {
            allRaces: this.calculatorRaces,
            allClasses: this.calculatorClasses,
            finalClass: this.calculatorFinalClass,
            finalRace: this.calculatorFinalRace,
            pageChanger: this.calculatorPageChanger,
            characterName: this.calculatorCharacterName,
            attributesModifiers: this.calculatorAttributesModifiers,
            attributesTotalScores: this.calculatorAttributesTotalScores,
            pointsLeft: 27,
            attributes: ['Strength', 'Dexterity', 'Constitution', 'Intelligence', 'Wisdom', 'Charisma'],
            attributesScores: {'Strength': 8 ,  'Dexterity': 8 , 'Constitution' : 8, 'Intelligence': 8 , 'Wisdom': 8, 'Charisma': 8},
            attributesPointScores: {'Strength': 0 ,  'Dexterity': 0 , 'Constitution' : 0, 'Intelligence': 0 , 'Wisdom': 0, 'Charisma': 0},
        }
    },
    methods: {
        openFinalSheet(){
            this.$emit('changePageAbilityCalc', 'finishedSheet');
            this.$emit('changeCharacterName', this.characterName);
            this.$emit('changeAttributesModifiers', this.attributesModifiers);
            this.$emit('changeAttributesTotalScores', this.attributesTotalScores);
        },
        checkRacialBonusesAmount(){
            if(this.allRaces['Half-Elf'].halfElfExtraAttrs.length < 2){
                return true;
            }else{
                return false;
            }
        },
        addToHalfElfRacialBonuses(newBonus){
            this.allRaces[this.finalRace].halfElfExtraAttrs.push(newBonus);
        },
        increasePointScore(attrValue, attrName){
            if(this.spendAttributePointsIncrease(attrValue, attrName)){
                this.attributesScores[attrName]++;
            }
        },
        spendAttributePointsIncrease(attrValue, attrName){
            if(attrValue >=  8 && attrValue <= 12){
                this.attributesPointScores[attrName]++;
                this.pointsLeft--;
            }else if(attrValue === 13 || attrValue === 14){
                if(this.pointsLeft === 1){
                    return false;
                }
                this.attributesPointScores[attrName]+=2;
                this.pointsLeft-=2;
            }
            return true;
        },
        decreasePointScore(attrValue, attrName){
            this.attributesScores[attrName]--;
            this.spendAttributePointsDecrease(attrValue, attrName);
        },
        spendAttributePointsDecrease(attrValue, attrName){
            if(attrValue >= 9 && attrValue <= 13){
                this.attributesPointScores[attrName]--;
                this.pointsLeft++;
            }else if(attrValue === 14 || attrValue === 15){
                this.attributesPointScores[attrName]-=2;
                this.pointsLeft+=2;
            }
        },
        getRaceBonus(ability, finalRace){
            if(this.allRaces[this.finalRace].racialBonus.hasOwnProperty(ability) === true){
                return this.allRaces[this.finalRace].racialBonus[ability];
            }else if(finalRace === 'Half-Elf' && this.allRaces[this.finalRace].halfElfExtraAttrs.includes(ability) === true){
                return 1;
            }else{
                return 0;
            }
        },
        getModifier(pointCounter, attribute){
            if(pointCounter === 8 || pointCounter === 9){
                this.attributesModifiers[attribute] = -1;
            }else if(pointCounter === 10 || pointCounter === 11){
                this.attributesModifiers[attribute] = 0;
            }else if(pointCounter === 12 || pointCounter === 13){
                this.attributesModifiers[attribute] = 1;
            }else if(pointCounter === 14 || pointCounter === 15){
                this.attributesModifiers[attribute] = 2;
            }else if(pointCounter === 16 || pointCounter === 17){
                this.attributesModifiers[attribute] = 3;
            }
            return this.attributesModifiers[attribute];
        },
        getTotalScore(raceBonus, attributeScore, attribute){
            let result = raceBonus + attributeScore;
            this.attributesTotalScores[attribute] = result;
            return result;
        },
    },
}
</script>
<style>
@import "../../node_modules/bootstrap/dist/css/bootstrap.min.css";
@import '../assets/main.css';
@import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Stencil+Display:wght@500&family=Fondamento&display=swap');
</style>