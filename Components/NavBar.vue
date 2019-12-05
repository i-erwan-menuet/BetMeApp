<template>
    <view class="menuContainer">
        <view class="navBar">
            <view class="navBarIcons">
                <touchable-opacity class="navElement navMenu" v-bind:on-press="goToHomePage">
                    <ionicons class="navElement" v-bind:style="getStyle(0)" name="ios-home" color="white"/>
                </touchable-opacity>
                <touchable-opacity class="navElement navMenu" v-bind:on-press="goToBetPage">
                    <ionicons class="navElement" v-bind:style="getStyle(1)" name="ios-albums" color="white"/>
                </touchable-opacity>
                <touchable-opacity class="navElement navMenu" v-bind:on-press="goToTransferPage">
                    <ionicons class="navElement" v-bind:style="getStyle(2)" name="ios-card" color="white"/>
                </touchable-opacity>
            </view>
            <text class="navPageName"> {{ currentPage.Name }}</text>
        </view>
    </view>
</template>

<script>
    export default {
        components:{
        },
        props:["currentPage", "pages"],
        data: function() {
            return {
                displaySideBar: false
            }
        },
        methods:{
            toggleSideBar: function(){
                this.displaySideBar = !this.displaySideBar;
            },
            closeSideBar: function(){
                this.displaySideBar = false;
            },

            goToHomePage: function(){
                this.goToPage(0);
            },
            goToBetPage: function(){
                this.goToPage(1);
            },
            goToTransferPage: function(){
                this.goToPage(2);
            },
            goToPage: function(index){
                this.$emit('go-to-page', index)
            },

            getStyle: function(index){
                let active = this.currentPage.Id == index;

                return {
                    color: active ? "#0066cc" : "white"
                }
            }
        }
    };
</script>

<style>
    /* #80bfff
       #3399ff
       darker: #0066cc
     */

    .menuContainer{
        width:100%;
        flex-basis: 50px;
    }

    .navBar{
        background-color: #3399ff;
        height:50px;
        justify-content: space-between;
        align-items: center;

        display: flex;
        flex-direction: row;

        border-bottom-color: #0066cc;
        border-bottom-width: 3px;
    }

    .navBarIcons{
        height:100%;

        flex-basis: 25%;
        flex-grow: 0;
        flex-shrink: 0;

        display:flex;
        flex-direction: row;
        align-items: center;
    }

    .navElement{
        color:white;
        font-size: 30px;
        margin:0;
    }

    .active{
        color:goldenrod;
    }

    .navMenu{
        height:100%;
        padding-top:11px;
        margin-left: 15px;
        /* border-bottom-color: orange;
        border-bottom-width: 2px; */
    }

    .navPageName{
        color:white;
        font-size: 22px;
        margin:0;

        flex-basis: 65%;
        flex-grow: 0;
        flex-shrink: 0;

        margin-right: 5px;

        text-align: right;
    }
</style>