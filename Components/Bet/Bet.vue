<template>
    <view class="betContainer">
        <text>{{bet.Title}}</text>
    </view>
</template>

<script>
export default {
    props:["bet"],
    data: function(){
        return {

        }
    },
    methods:{

    }
}
</script>

<style>
.betContainer{
    height:85px;
    width:100%;
    border-radius: 2px;
    border-color: gray;
    border-width: 1px;
    margin-bottom: 10px;
}
</style>