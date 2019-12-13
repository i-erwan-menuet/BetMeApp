<template>
    <view class="formContainer">
        <text class="formTitle">Ajout d'un pari</text>
        <view class="separation-line"></view>
        <text-input class="text-input" placeholder="Nom du pari" v-model="newBet.Title"/>
        <text-input class="text-input" placeholder="Montant" v-model="newBet.Amount"/>
        <text-input class="text-input" placeholder="Côte" v-model="newBet.Cote"/>
        <!-- <view class="separation-line"></view> -->
        <text-input class="text-input" placeholder="Bookmaker" v-model="newBet.Bookmaker"/>
        <text-input class="text-input" placeholder="Status" v-model="newBet.Status"/>
        
        <view class="separation-line"></view>
        <button v-bind:onPress="saveBet" title="Sauvegarder"/>
    </view>
</template>

<script>
export default {
    props:['i'],
    data: function(){
        return {
            betPlateform: ['Betclic', 'Unibet', 'Winamax', 'Parions Sport'],
            newBet: {
                Title: "Test",
                Status: "Test",
                Cote: "Test",
                Bookmaker: "Test",
                Amount: "Test"
            }
        }
    },
    methods:{
        saveBet: function(){
            this.$emit('save', this.newBet);
            this.resetNewBet();
        },
        resetNewBet: function(){
            this.newBet.Title = "Test" + this.i;
            // this.newBet.Status = "";
            // this.newBet.Cote = "";
            // this.newBet.Bookmaker = "";
            // this.newBet.Amount = "";
        }
    }
}
</script>

<style>
.formContainer{
    height:100%;
    width:100%;
    text-align: center;
    display:flex;
    flex-direction: column;
    align-items: center;
}

.formTitle{
    flex-basis: 50px;
    font-size: 25px;
    color:#3399ff;
    text-align: center;
}

.text-input{
  width: 70%;
  height: 40;
  font-size: 22;
  border-width: 1px;
  border-radius: 3px;
  border-color: #99ccff;
  margin-bottom: 3px;
  padding:2px;
}

.separation-line{
    flex-basis: 10px;
    width: 85%;
    color:#3399ff;
}
</style>