<template>
  <view class="container">
    <StatusBar v-bind:color="statusBarColor"/>
    <NavBar v-bind:current-page="currentPage" v-on:toggle="toggleSideBar"/>
    <SideBar v-if="displaySideBar" v-on:close="closeSideBar"
             v-bind:current="currentPage.Id" v-bind:pages="pages" v-on:go-to-page="goToPage"/>    
    
    <view v-if="currentPage.Id == 0">
      <HomePage/>
    </view>
    
    <view v-if="currentPage.Id == 1">
      <BetPage/>
    </view>

    <view v-if="currentPage.Id == 2">
      <TransferPage/>
    </view>
  </view>
</template>

<script>
    //import { Ionicons } from "react-native-elements"
    import { Ionicons } from "@expo/vector-icons";
    import Vue from "vue-native-core";

    Vue.component("ionicons", Ionicons);

    import StatusBar from "./Components/StatusBar.vue";
    import NavBar from "./Components/NavBar.vue";
    import SideBar from "./Components/SideBar.vue";

    import HomePage from "./Components/HomePage.vue";
    import BetPage from "./Components/BetPage.vue";
    import TransferPage from "./Components/TransferPage.vue";

    export default{
      components:{
        StatusBar,
        NavBar,
        SideBar,
        HomePage,
        BetPage,
        TransferPage,
        Ionicons
      },
      mounted: function(){
        this.goToPage(0);
      },
      data (){
        return{
            statusBarColor: "white",
            currentPage: {},
            pages:[
              {
                  Id: 0,
                  Name: "Home"
              },
              {
                  Id: 1,
                  Name: "Add a bet"
              },
              {
                  Id: 2,
                  Name: "Add a transfert"
              }
            ],
            displaySideBar: false
        };
      },
      methods:{
        goToPage: function(index){
          this.currentPage = this.pages[index];
        },
        toggleSideBar: function() {
          this.displaySideBar = !this.displaySideBar;
        },
        closeSideBar: function(){
          this.displaySideBar = false;
        }
      }
    }
</script>


<style>
.container {
  /*background-color: white;*/
  flex: 1;
}
</style>
