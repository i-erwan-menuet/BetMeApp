<template>
    <view class="navBar">
        <touchable-opacity class="navElement navMenu" v-bind:on-press="toggleSideBar">
            <ionicons class="navElement" name="ios-menu" color="white"/>
        </touchable-opacity>
        <text class="navElement navPageName"> {{ currentPage.Name }}</text>
    </view>
</template>

<script>
    export default {
        props:["currentPage"],
        data: function() {
            return {
            }
        },
        methods:{
            toggleSideBar: function(){
                this.$emit("toggle");
            }            
        }
    };
</script>

<style>
    .navBar{
        background-color: #3399ff;
        height:50px;
        justify-content: center;
        align-items: center;

        display: flex;
        flex-direction: row;
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
</style>