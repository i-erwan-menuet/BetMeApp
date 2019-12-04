<template>
    <view class="fullContainer">
        <view class="sideBar">
            <text class="menuItem menuHeader menuText"> Menu </text>
            <touchable-opacity v-bind:on-press="goToHome" class="menuButton">
                <text class="menuItem menuText" v-bind:class="{ 'active-item': 0 == current}">{{pages[0].Name}}</text>
            </touchable-opacity>
            <touchable-opacity v-bind:on-press="goToBetForm" class="menuButton">
                <text class="menuItem menuText" v-bind:class="{ 'active-item': 1 == current}">{{pages[1].Name}}</text>
            </touchable-opacity>
            <touchable-opacity v-bind:on-press="goToTransferForm" class="menuButton">
                <text class="menuItem menuText" v-bind:class="{ 'active-item': 2 == current}">{{pages[2].Name}}</text>
            </touchable-opacity>
        </view>
        <touchable-opacity class="overlay" v-bind:on-press="closeSideBar"></touchable-opacity>
    </view>
</template>

<script>
export default {
    props:['current', 'pages'],
    data: function(){
        return {

        }
    },
    methods:{
        closeSideBar: function(){
            this.$emit("close");
        },
        goToHome: function(){
            this.goToIndex(0);
        },
        goToBetForm: function(){
            this.goToIndex(1);
        },
        goToTransferForm: function(){
            this.goToIndex(2);
        },
        goToIndex: function(index){
            this.$emit('go-to-page', index);
            this.closeSideBar();
        }
    }
}
</script>

<style>
    .fullContainer{
        width: 100%;
        height: 100%;
    }

    .sideBar{
        position:absolute;
        top:0;
        left:0;
        width: 55%;
        height: 100%;
        z-index: 100;
        background-color: #80bfff;

        display:flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
    }

    .overlay{
        position:absolute;
        top:0;
        right: 0;
        width: 45%;
        height: 100%;
        z-index: 90;
        background-color: black;
        opacity: 0.2;
    }

    .menuItem{
        flex-basis: 50px;
        width: 100%;
        text-align: center;
        line-height: 50px;
    }

    .menuHeader{
        background-color: #3399ff;
    }

    .menuButton{
        width:100%;
    }

    .menuText{
        color:white;
        text-align: center;
        font-size: 25px;
    }

    .active-item{
        color: orange;
    }

</style>