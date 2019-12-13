<template>




    <div id="app">
        <Menu v-bind:menuItems="menuItems"/>


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
          label: "Plots",
            content: Plots,
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
              label:"Bfmi",
                content : Diagnosis.options[0]
            },
            {
              label:"Ess",
                content : Diagnosis.options[1]
            },
            {
              label:"Rhat",
                content : Diagnosis.options[2]
            },
            {
              label:"Mcse",
                content : Diagnosis.options[3]

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
