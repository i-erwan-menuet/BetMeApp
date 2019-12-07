<template>
  <view class="container">
    <StatusBar v-bind:color="statusBarColor"/>
    <NavBar v-bind:current-page="currentPage" v-bind:pages="pages" v-on:go-to-page="goToPage"/>  
    
    <view class="page">
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
    <!-- <view class="footer"></view> -->
  </view>
</template>

<script>
    //import { Ionicons } from "react-native-elements"
    import { Ionicons } from "@expo/vector-icons";
    import Vue from "vue-native-core";
    import vSelect from 'vue-select'

    Vue.component('v-select', vSelect)
    import 'vue-select/dist/vue-select.css';

    Vue.component("ionicons", Ionicons);

    import StatusBar from "./Components/StatusBar.vue";
    import NavBar from "./Components/NavBar.vue";

    import HomePage from "./Components/HomePage.vue";
    import BetPage from "./Components/BetPage.vue";
    import TransferPage from "./Components/TransferPage.vue";

    export default{
      components:{
        StatusBar,
        NavBar,
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
                  Name: "Dashboard"
              },
              {
                  Id: 1,
                  Name: "Paris"
              },
              {
                  Id: 2,
                  Name: "Transferts"
              }
            ],
            displaySideBar: false
        };
      },
      methods:{
        goToPage: function(index){
          this.currentPage = this.pages[index];
        }
      }
    }
</script>


<style>
  .container {
    /*background-color: white;*/
    flex: 1;
    display: flex;
    flex-direction: column;
  }

  .page{
    flex-basis: auto;
    padding:10px 15px;
    flex-grow: 1;
    flex-shrink: 1;
  }

  .footer{
    flex-basis: 20px;
    width:100%;
    background-color: #3399ff;
  }
</style>
