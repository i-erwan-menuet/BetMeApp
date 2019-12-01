<template>
  <view class="menuContainer">
    <view class="navBar" v-bind:style="getStyle()">
        <touchable-opacity class="navElement navMenu" v-bind:on-press="displaySideBar">
            <ionicons class="navElement" name="ios-menu" color="white"/>
        </touchable-opacity>
        <text class="navElement navPageName"> {{ title }}</text>
    </view>
    <view class="sideBar" v-if="sideBarDisplayed">
        <touchable-opacity class="closeMenu menuItem" v-bind:on-press="closeSideBar">
            <ionicons class="closeMenu" name="ios-close" color="white"/>
        </touchable-opacity>

        <touchable-opacity v-for="(link, index) in menuLinks" v-bind:key="index" class="menuItem">
            <text class="menuText">{{ link.Name }}</text>
        </touchable-opacity>

    </view>
  </view>
</template>

<script> 
    export default {
        props:['title'],
        data: function() {
            return {
                sideBarDisplayed: false,
                menuLinks:[
                    {
                        Id: "Home",
                        Name: "Home"
                    },
                    {
                        Id: "AddBet",
                        Name: "Add a bet"
                    },
                    {
                        Id: "AddTransfert",
                        Name: "Add a transfert"
                    }
                ]
            };
        },
        methods:{
            getStyle: function(){
                return {
                }
            },
            displaySideBar: function(){
                this.sideBarDisplayed = true;
            },
            closeSideBar: function(){
                this.sideBarDisplayed = false;
            },

            openLink: function(link, index){
                alert("You clicked on " + link.Name + ". Link n°" + index);
            }
        }
    };
</script>

<style>
    .menuContainer{
        width: 100%;
        height: 100%;
    }

    .navBar{
        background-color: black;
        height:50px;
        justify-content: center;
        align-items: center;

        display: flex;
        flex-direction: row;

        border-bottom-color: green;
        border-bottom-width: 1px;
    }

    .navElement{
        color:white;
        font-size: 30px;
        margin:0;
        text-align: center;
    }

    .navMenu{
        margin-top: 3px;
        flex-basis: 5%;
    }

    .navPageName{
        flex-basis: 90%;
        text-align: right;
    }

    .sideBar{
        position:absolute;
        top:0;
        left:0;
        width: 55%;
        height: 100%;
        z-index: 100;
        background-color: black;
        border-right-color: white;
        border-right-width: 1px;

        display:flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
    }

    .menuItem{
        flex-basis: 50px;
        border-bottom-color: white;
        border-bottom-width: 1px;
        width: 100%;
        text-align: center;
    }

    .menuText{
        color:white;
        text-align: center;
        font-size: 25px;
    }

    .closeMenu{
        color:white;
        font-size: 35px;
        text-align: center;
    }
</style>