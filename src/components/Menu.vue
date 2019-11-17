<template>
    <div>
        <div class="menu">
            <h1>{{Stats}}</h1>
        <div v-bind:key="item.label" v-for="item in menuItems">

            <h3>{{item.label}}</h3>
            <h1>{{Diagnosis}}</h1>

        </div></div>
    </div>
</template>

<script>
    export default {
        name: "menu",
        props: ["menuItems", "Diagnosis", "Stats"],

    }
</script>

<style scoped>
    template{

    }
    .menu{
        background: aqua;
        height: 970px;
        width: 30%;
    }

</style>