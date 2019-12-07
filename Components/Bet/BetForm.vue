<template>
    <view class="formContainer">
        <text class="formTitle">Ajout d'un pari</text>
        <view class="separation-line"></view>
        <text-input class="text-input" placeholder="Nom du pari" v-model="newBet.Name"/>
        <v-select v-bind:options="betPlateform"></v-select>
        <text-input class="text-input" placeholder="Montant" v-model="newBet.Price"/>
        <text-input class="text-input" placeholder="Côte" v-model="newBet.Cote"/>
    </view>
</template>

<script>
export default {
    props:['newBet'],
    data: function(){
        return {
            betPlateform: ['Betclic', 'Unibet', 'Winamax', 'Parions Sport']
        }
    },
    methods:{

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
  border-color: #f2f2f2;
}

.separation-line{
    flex-basis: 1px;
    width: 85%;
    color:#3399ff;
}
</style>