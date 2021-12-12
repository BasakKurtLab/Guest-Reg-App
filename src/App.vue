<template>
    <div class="container">
        <h1 class="text-center">Guest registration form</h1>
        <hr>
        <NewPerson></NewPerson>
        <br><br>
       
        
        <Persons></Persons>
    </div>
</template>

<script>
    import NewPerson from "./components/NewPerson.vue"
    import Persons from "./components/Persons.vue";

    export default {
        components: {
            NewPerson,
            Persons
        },

    }
</script>
<style>
    body {
        background-color: rgb(190, 216, 236);
        padding-top: 20px;
        padding-bottom: 20px;
    }

    .card {
        margin-right: 5px;
        margin-bottom: 5px;
        border-radius: 10px;
      
        box-shadow: 1px 1px 20px 3px rgba(25, 32, 128, 0.651);
    }

    .card:last-child {
        margin-right: 0px;
    }

    .col-md-2 {
        max-width: 15.666667% !important;
    }

    .product-container {
        display: flex;
        justify-content: center;
        
    }

</style>

