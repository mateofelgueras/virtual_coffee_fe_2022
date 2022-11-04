<template>
  <div id="homepage">
    <Header/>

    <div id="home-container">
      <div>
        <SideBar @menu-event="showMenuOptionSelected"/>
      </div>

      <div>
        <Home v-if="menu.home" v-on:menuEvent="showMenuOptionSelected"/>
        <beverage-menu v-if="menu.beverage"/>
        <snack-menu v-if="menu.snacks"/>
        <order-online v-if="menu.order"/>
      </div>

      <div id="div-banner">
        <banner-comp/>
      </div>
    </div>

    <Footer/>
  </div>
</template>

<script>
import Header from "@/components/Header";
import Footer from "@/components/Footer";
import SideBar from "@/components/SideBar";
import Home from "@/components/Home";
import BannerComp from "@/components/Banner";
import BeverageMenu from "@/components/BeverageMenu";
import SnackMenu from "@/components/SnackMenu";
import OrderOnline from "@/components/OrderOnline";

export default {
  name: "HomeView",
  components: {
    OrderOnline,
    SnackMenu,
    BeverageMenu,
    BannerComp,
    SideBar,
    Header,
    Footer,
    Home,
  },
  data() {
    return {
      menu: {
        activeOption: "home",
        home: true,
        beverage: false,
        snacks: false,
        order: false,
      }
    }
  },
  methods: {
    showMenuOptionSelected(option) {
      let oldOption = this.menu.activeOption;
      this.menu.activeOption = option;
      this.menu[oldOption] = false;
      this.menu[this.menu.activeOption] = true;
    }
  },
}
</script>

<style scoped>
#homepage {
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  height: 98vh;
}
#home-container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
}
#div-banner {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
}
</style>