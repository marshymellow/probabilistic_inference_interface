<template>
    <div>
        <div class="menu">
            <b-list-group>
                <b-list-group-item><h3>{{menuItems[0].label}}</h3></b-list-group-item>
                <b-list-group-item><h3>{{menuItems[1].label}}</h3></b-list-group-item>
                <b-list-group-item>{{menuItems[1].sub_options[0].label}}</b-list-group-item>
                <b-list-group-item>{{menuItems[1].sub_options[1].label}}</b-list-group-item>
                <b-list-group-item>{{menuItems[1].sub_options[2].label}}</b-list-group-item>
                <b-list-group-item>{{menuItems[1].sub_options[3].label}}</b-list-group-item>
                <b-list-group-item><h3>{{menuItems[2].label}}</h3></b-list-group-item>
                <b-list-group-item > {{menuItems[2].sub_options[0].label}}</b-list-group-item>
                <b-list-group-item active>{{menuItems[2].sub_options[1].label}}</b-list-group-item>
                <b-list-group-item>{{menuItems[2].sub_options[2].label}}</b-list-group-item>
                <b-list-group-item>{{menuItems[2].sub_options[3].label}}</b-list-group-item>

            </b-list-group>



        </div>
        <div class="output">
            <div>

                <b-table striped hover :items="items"></b-table>

            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "menu",
        props: ["menuItems", "Diagnosis", "Stats"],
        data() {
            return {
                items: [

                    { Dimensions: "school:8", Coordinates: "'Choate' 'Deerfield' ...St Paul", Mu: "float64 2.353e+03",
                    Theta_t: "float64 2.215e+03 3.157e+03 ... 2.679e+03 2.522e+03", Tau: "float64 1.268e+03",
                    Theta : "float64 2.298e+03 2.432e+03 ... 2.173e+03 2.277e+03"},

                ]
            }
        }

    }


</script>

<style scoped>
    template{

    }
    .menu{

        height: 970px;
        width: 30%;
    }

    .output{
        position: absolute;
        top: 0;
        left: 31%;


    }

</style>