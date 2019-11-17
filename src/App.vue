<template>
    <!-- <Menu v-bind:menuItems="menuItems"/>
    {{menuItems[1].label}} -->



    <div id="app">
        <Menu v-bind:menuItems="menuItems"/>
        {{menuItems[1].label}}

        {{menuItems}}
        {{Diagnosis }}

  </div>


</template>

<script>
  import Menu from "@/components/Menu";
  import Diagnosis from "@/assets/diagnosis.json"
  import Plots from "@/assets/plots.json"
  import Stats from "@/assets/stats.json"


export default {
  name: 'app',
  components: {
    Menu,

  },


  data(){
    return{
        Diagnosis : Diagnosis,
        Plots : Plots,
        Stats : Stats,
        menuItems: [
        {
          label: "Plots"
        },
        {
          label: "Stats",
          sub_options:[
            {
              label:"Test Function"
            },
            {
              label:"Loo"
            },
            {
              label:"Summary"
            },
            {
              label:"Waic"
            }
          ]
        },
        {
          label: "Diagnosis",
          sub_options:[
            {
              label:"Bfmi"
            },
            {
              label:"Ess"
            },
            {
              label:"Rhat"
            },
            {
              label:"Mcse"
            }
          ]
        }
      ]

    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;

}
</style>
