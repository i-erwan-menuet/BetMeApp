<template>
  <view class="statusBar" v-bind:style="getStyle()"></view>
</template>

<script>
  export default {
    props:['color'],
    data: function() {
      return {
      };
    },
    methods:{
      getStyle: function(){
        return {
          backgroundColor: this.color
        }
      }
    }
  };
</script>

<style>
  .statusBar{
    /*background-color: white;/*By default*/
    height:20px;
  }
</style>