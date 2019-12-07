<template>
    <view id="betPage">
        <touchable-opacity v-bind:on-press="toggleForm">
            <ionicons v-if="!displayAddForm" name="ios-add-circle" class="add-bet" color="#3399ff"></ionicons>
            <ionicons v-else name="ios-close-circle" class="add-bet" color="red"></ionicons>
        </touchable-opacity>
        
        <BetForm v-if="displayAddForm" v-bind:new-bet="newBet"/>

        <scroll-view id="betList">
            <Bet v-for="(bet, index) in bets" v-bind:key="index" v-bind:bet="bet"/>
            <view class="empty"></view>
        </scroll-view>
    </view>
</template>

<script>

import Bet from "./Bet/Bet.vue";
import BetForm from "./Bet/BetForm.vue";


export default {
    components:
    {
        Bet,
        BetForm
    },
    props:["currentPage", "pages"],
    data: function() {
        return {
            displayAddForm: false,
            bets:[
                {
                    Title: "Bet 1",
                    Status: "Success"
                },
                {
                    Title: "Bet 2",
                    Status: "Failed"
                }
            ],
            newBet: {

            }
        }
    },
    methods:{
        toggleForm: function(){
            this.displayAddForm = !this.displayAddForm;
        },
        closeForm: function(){
            this.displaySideBar = false;
        },
    }
}
</script>

<style>

#betPage{
    display:flex;
    flex-direction: column;
    justify-content: space-around;
    align-content: center;
}

.add-bet{
    flex-basis: 5%;
    align-self: flex-end;

    font-size:30px;
    margin-bottom: 5px;
}

#betList{
    flex-basis: 85%;
}

.empty{
    height:50px;
}
</style>