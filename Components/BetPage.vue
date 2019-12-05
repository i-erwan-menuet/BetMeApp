<template>
    <view id="betPage">
        <ionicons name="ios-add-circle" class="add-bet"></ionicons>
        
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
            displaySideBar: false,
            bets:[
                {
                    Title: "Bet 1",
                    Status: "Success"
                },
                {
                    Title: "Bet 2",
                    Status: "Failed"
                },
                {
                    Title: "Bet 1",
                    Status: "Success"
                },
                {
                    Title: "Bet 2",
                    Status: "Failed"
                },
                {
                    Title: "Bet 1",
                    Status: "Success"
                },
                {
                    Title: "Bet 2",
                    Status: "Failed"
                },
                {
                    Title: "Bet 1",
                    Status: "Success"
                },
                {
                    Title: "Bet 2",
                    Status: "Failed"
                },
                {
                    Title: "Bet 1",
                    Status: "Success"
                },
                {
                    Title: "Bet 2",
                    Status: "Failed"
                },
                {
                    Title: "Bet 1",
                    Status: "Success"
                },
                {
                    Title: "Bet 2",
                    Status: "Failed"
                },
                {
                    Title: "Bet 1",
                    Status: "Success"
                },
                {
                    Title: "Bet 2",
                    Status: "Failed"
                }
            ]
        }
    },
    methods:{
        toggleForm: function(){
            this.displaySideBar = !this.displaySideBar;
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
    color:#3399ff;
    margin-bottom: 5px;
}

#betList{
    flex-basis: 85%;
}

.empty{
    height:50px;
}
</style>