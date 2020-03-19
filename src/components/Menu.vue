<template>
    <div>
        <div class="menu">
            <b-list-group>
                <p class="mother">Plots</p>
                <b-list-group-item
                        v-for="(pitem, index) in pitems" :key="index"
                        @click="selectOption(index)"
                        :class="[selectedIndex === index ? 'selected': '']">
                                   {{pitem}}


                </b-list-group-item>
                <p class="mother">Diagnosis</p>
                <b-list-group-item
                        v-for="(ditem, index) in ditems" :key="index+6"
                        @click="selectOption(index+6)"
                        :class="[selectedIndex === index+6 ? 'selected': '']">
                    {{ditem}}


                </b-list-group-item>
                <p class="mother">Stats</p>
                <b-list-group-item
                        v-for="(sitem, index) in sitems" :key="index+10"
                        @click="selectOption(index+10)"
                        :class="[selectedIndex === index+10 ? 'selected': '']">
                    {{sitem}}


                </b-list-group-item>



            </b-list-group>



        </div>
        <div class="output">

                <p v-if="selectedIndex==0">
                   <img src="@/assets/plot_autocorr.png"/>
                </p>

                <p v-if="selectedIndex==1">

                    <img src="@/assets/plot_energy.png"/>

                </p>
                <p v-if="selectedIndex==2">

                    <img src="@/assets/plot_density.png"/>
                </p>
            <p v-if="selectedIndex==3">

                <img src="@/assets/plot_ess.png"/>
            </p>
            <p v-if="selectedIndex==4">

                <img src="@/assets/plot_msce.png"/>
            </p>
            <p v-if="selectedIndex==5">

                <img src="@/assets/plot_rank.png"/>
            </p>

            <p v-if="selectedIndex==6">

                    <b-table bordered striped  :items="bfmi" ></b-table>
            </p>
            <p v-if="selectedIndex==7">

                <b-table striped bordered  :items="ess_dimensions"></b-table>
                <b-table striped bordered :items="ess_coordinates"></b-table>
                <b-table striped bordered :items="ess_datavar"></b-table>
            </p>
            <p v-if="selectedIndex==8">

                <b-table striped bordered  :items="rhat_dimensions"></b-table>
                <b-table striped bordered :items="rhat_coordinates"></b-table>
                <b-table striped bordered :items="rhat_datavar"></b-table>
            </p>
            <p v-if="selectedIndex==9">

                <b-table striped bordered  :items="mcse_dimensions"></b-table>
                <b-table striped bordered :items="mcse_coordinates"></b-table>
                <b-table striped bordered  :items="mcse_datavar"></b-table>
            </p>

            <p v-if="selectedIndex==10">

                <b-table striped bordered  :items="loo"></b-table>

            </p>
            <p v-if="selectedIndex==11">

                <b-table striped bordered  :items="waic" :fields="waic_fields"></b-table>

            </p>


            </div>
        </div>
    </div>
</template>

<script>

    export default {
        name: "menu",
        props: ["menuItems", "Diagnosis", "Stats","Plots"],
        data() {
            return {
                bfmi: [

                    {   BFMI: "Array",
                        " ":"0.17190733, 0.16926329, 0.09424201, 0.07138791"

                    },

                ],
                ess_dimensions: [
                    {
                        Ess_Dimensions: "Country",
                        " ":"85"
                    },
                    {
                        Ess_Dimensions: "Gamma_Dim_0",
                        " ":"3"
                    },
                    {
                        Ess_Dimensions: "observed_county",
                        " ":"919"
                    }
                ],
                ess_coordinates:[
                    {
                        Ess_Coordinates:"gamma_dim_0",
                        " ":"int64 0 1 2"

                    },
                    {
                        Ess_Coordinates:"county",
                        " ":"'AITKIN' 'ANOKA' ... 'YELLOW MEDICINE'"

                    },
                    {
                        Ess_Coordinates:"observed_county",
                        " ":"'AITKIN' ... 'YELLOW MEDICINE'"

                    },
                ],
                ess_datavar:[
                    {
                        Ess_data_variables:"Gamma",
                        " ":"1.106e+03 1.203e+03 1.393e+03"
                    },
                    {
                        Ess_data_variables:"Eps_a",
                        " ":"2.848e+03 1.668e+03 ... 645.0 2.777e+03"
                    },
                    {
                        Ess_data_variables:"b",
                        " ":"1.853e+03"
                    },
                    {
                        Ess_data_variables:"sigma_a ",
                        " ":"36.2"
                    },
                    {
                        Ess_data_variables:"mu_a ",
                        " ":"948.4 948.4 ... 1.167e+03"
                    },
                    {
                        Ess_data_variables:"a ",
                        " ":"3.076e+03 3.076e+03 ... 2.618e+03"
                    },
                    {
                        Ess_data_variables:"sigma_y",
                        " ":"1.437e+03"
                    },

                ],
                rhat_dimensions: [
                    {
                        rhat_Dimensions: "Country",
                        " ":"85"
                    },
                    {
                        rhat_Dimensions: "Gamma_Dim_0",
                        " ":"3"
                    },
                    {
                        rhat_Dimensions: "observed_county",
                        " ":"919"
                    }
                ],
                rhat_coordinates:[
                    {
                        rhat_Coordinates:"gamma_dim_0",
                        " ":" 0 1 2"

                    },
                    {
                        rhat_Coordinates:"county",
                        " ":"'AITKIN' 'ANOKA' ... 'YELLOW MEDICINE'"

                    },
                    {
                        rhat_Coordinates:"observed_county",
                        " ":"'AITKIN' ... 'YELLOW MEDICINE'"

                    },
                ],
                rhat_datavar:[
                    {
                        Rhat_data_variables:"Gamma",
                        " ":"1.004 1.003 1.0"
                    },
                    {
                        Rhat_data_variables:"Eps_a",
                        " ":"1.015 1.008 1.018 ... 1.018 1.008 1.012"
                    },
                    {
                        Rhat_data_variables:"b",
                        " ":"1.002"
                    },
                    {
                        Rhat_data_variables:"sigma_a ",
                        " ":"1.081"
                    },
                    {
                        Rhat_data_variables:"mu_a ",
                        " ":"1.006 1.006 1.006 ... 1.004 1.004"
                    },
                    {
                        Rhat_data_variables:"a ",
                        " ":"1.014 1.014 1.014 ... 1.009 1.009"
                    },
                    {
                        Rhat_data_variables:"sigma_y",
                        " ":"1.003"
                    },

                ],
                mcse_dimensions: [
                    {
                        mcse_Dimensions: "Country",
                        " ":"85"
                    },
                    {
                        mcse_Dimensions: "Gamma_Dim_0",
                        " ":"3"
                    },
                    {
                        mcse_Dimensions: "observed_county",
                        " ":"919"
                    }
                ],
                mcse_coordinates:[
                    {
                        mcse_coordinates:"gamma_dim_0",
                        " ":" 0 1 2"

                    },
                    {
                        mcse_coordinates:"county",
                        " ":"'AITKIN' 'ANOKA' ... 'YELLOW MEDICINE'"

                    },
                    {
                        mcse_coordinates:"observed_county",
                        " ":"'AITKIN' ... 'YELLOW MEDICINE'"

                    },
                ],
                mcse_datavar:[
                    {
                        mcse_data_variables:"Gamma",
                        " ":"0.00141 0.002486 0.004985"
                    },
                    {
                        mcse_data_variables:"Eps_a",
                        " ":"0.002225 0.002175 ... 0.00472 0.002449"
                    },
                    {
                        mcse_data_variables:"b",
                        " ":"001652"
                    },
                    {
                        mcse_data_variables:"sigma_a ",
                        " ":"006672"
                    },
                    {
                        mcse_data_variables:"mu_a ",
                        " ":"0.002126 0.002126 ... 0.001725"
                    },
                    {
                        mcse_data_variables:"a ",
                        " ":"0.002364 0.002364 ... 0.002684"
                    },
                    {
                        mcse_data_variables:"sigma_y",
                        " ":"0.0004753"
                    },

                ],
                loo:[
                    {
                        " ":"IC_loo",
                        estimate:"2053,28",
                        SE:"58.58"

                    },
                    {
                        " ":"p_loo ",
                        estimate:"23.27",
                        SE:" -"

                    }
                ],
                waic:[
                    {
                        " ":"IC_waic",
                        estimate:"2052.95",
                        SE:"58.51",


                    },
                    {
                        " ":"p_waic ",
                        estimate:"23.11",
                        SE:" -"

                    }
                ],
                waic_fields: [
                    {
                        key: ' ',

                    },
                    {
                        key: 'estimate',
                        variant: 'danger'

                    },
                    {
                        key: 'SE',

                        // Variant applies to the whole column, including the header and footer
                        variant: 'danger'
                    }],




                selectedIndex: null,

            }
        },
        computed:{
            pitems(){
                let pitems=[]
                pitems.push(
                    "Autocorr","Energy","Density","Ess","Mcse","Rank",

                );

                return pitems

            },
            ditems(){
                let ditems=[]
                ditems.push(

                    "Bfmi", "Ess","Rhat", "Mcse",

                );

                return ditems

            },
            sitems(){
                let sitems=[]
                sitems.push(
                    "Loo", "Waic","Summary",
                );

                return sitems

            }
        },
        watch:{
            currentOption:{
                immediate: true,
                handler() {
                    this.selectedIndex = null


                }

            }
        },
        methods:{
            selectOption(index){
                this.selectedIndex=index
            },


            }

    }


</script>

<style scoped>
    template{

    }
    .menu{


        width: 30%;
        background-color: #292d3e ;

    }

    .output{
        position: absolute;
        top: 0;
        left: 31%;


    }
    .mother{
        color: #71b3d5;
        font-size: 25px;
        margin-left: 5px;


    }


    .list-group-item{
        color: #71b3d5;
        background-color: #292d3e ;
    }
    .list-group-item:hover{
        background: #232235;
        cursor: pointer;
    }
    .selected{
        background-color: #232235;
    }

    .correct{
        background-color: lightgreen;
    }

    .incorrect{
        background-color: red;
    }


</style>