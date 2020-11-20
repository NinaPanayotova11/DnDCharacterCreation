<template>
    <div class="finishedSheet">
            <div class="row">
                <div class="container final-sheet-container">
                    <div class="row final-page-title-div">
                          <h1 class="final-page-title">{{characterName}}</h1>
                          <h3 class="final-page-title final-page-title-small">Race: {{finalRace}}</h3>
                          <h3 class="final-page-title final-page-title-small">Class: {{finalClass}}</h3>
                    </div>
                    <div class="row">
                        <div class = "col-9 scores-and-modifiers-div">
                            <div class="row">
                                <div class="col-4">
                                <h4 class="final-sheet-titles">Ability</h4>
                                </div>
                                <div class="col-4">
                                <h4 class="final-sheet-titles">Score</h4>
                                </div>
                                <div class="col-4">
                                <h4 class="final-sheet-titles">Modifier</h4>
                                </div>
                            </div>
                            <div v-for="(value, name) in attributesTotalScores"  v-bind:key="name" class="row">
                                <div class="col-4">
                                <h5 class="final-sheet-info">{{name}}:</h5>
                                </div>
                                <div class="col-4">
                                <h5 class="final-sheet-info">{{value}}</h5>
                                </div>
                                <div class="col-4">
                                <h5 class="final-sheet-info">{{attributesModifiers[name]}}</h5>
                                </div>
                            </div>
                        </div>
                        <div class="col-3 saving-throws-div">
                            <div class="row">
                                <div class="col-12">
                                    <h4 class="final-sheet-titles">Saving Throws</h4>
                                </div>
                            </div>
                            <div class="row">
                                <div v-for="(savingThrow, attribute) in savingThrows" v-bind:key="attribute" class="col-12">
                                    <h5 class="final-sheet-info">{{attribute}}: {{savingThrow}}</h5>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="row final-sheet-explanation">
                        <h5>*Your Saving Throw for each Ability is equal to your Ability Modifier. If the Class you have chosen has Proficiency in that Saving Throw, the Saving Throw is equal to the sum of the Ability Modifier and the Proficiency Bonus. Both your Proficiency Bonus and the Saving Throws, you are proficient with, are shown in the page of your Class.</h5>
                    </div>
                </div>
            </div>
        </div>
</template>
<script>
    export default {
        name: 'FinishedSheet',
        props: {
            finishedSheetFinalClass: String,
            finishedSheetFinalRace: String,
            finishedSheetCharacterName: String,
            finishedSheetAttributesModifiers: Object,
            finishedSheetAttributesTotalScores: Object,
            finishedSheetSavingThrows: Object
        },
        data(){
            return {
                finalClass: this.finishedSheetFinalClass,
                finalRace: this.finishedSheetFinalRace,
                characterName: this.finishedSheetCharacterName,
                attributesModifiers: this.finishedSheetAttributesModifiers,
                attributesTotalScores: this.finishedSheetAttributesTotalScores,
                savingThrows: this.finishedSheetSavingThrows
            }
        },
    }
</script>
<style>
    @import "../../node_modules/bootstrap/dist/css/bootstrap.min.css";
    @import '../assets/main.css';
    @import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Stencil+Display:wght@500&family=Fondamento&display=swap');
</style>