<template>
  <view class="container">
    <StatusBar v-bind:color="statusBarColor"/>
    <NavBar v-bind:title="currentTitle"/>
  </view>
</template>

<script>
    //import { Ionicons } from "react-native-elements"
    import { Ionicons } from "@expo/vector-icons";
    import Vue from "vue-native-core";

    Vue.component("ionicons", Ionicons)

    import StatusBar from "./Components/StatusBar.vue"
    import NavBar from "./Components/NavBar.vue"

    export default{
      components:{
        StatusBar,
        NavBar,
        Ionicons
      },
      data (){
        return{
            statusBarColor: "green",
            currentTitle: "Home"
        };
      }
    }
</script>


<style>
.container {
  /*background-color: white;*/
  flex: 1;
}
</style>
