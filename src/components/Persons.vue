<template>
    <div v-if="personList.length > 0">
        <h3 class="text-center">Guests List</h3>
        <hr>
        <div class="row product-container">
            <Person v-for="person in personList" :key="person.index">
                <img class="card-img-top" :src="person.selectedImage" :alt="person.name">
                <div class="card-body">
                    <h5 class="card-title"> {{ person.name }} </h5>
                    <small><strong>Name : </strong> {{ person.name }}</small>
                    <br>
                    <small><strong>City : </strong> {{ person.city }}</small>
                    <br>
                    <small><strong>Birth : </strong> {{ person.birth }}</small>
                    <br><br>
                    <button class="btn btn-danger btn-block" @click="del(index)"> Delete </button>
                </div>
                
            </Person>
        </div>
    </div>
</template>

<script>
    import {eventBus} from "../main";
    import Person from "./Person.vue";

    export default {
        components: {
            Person
        },
        data() {
            return {
                personList: [],
                
            }
        },
        methods: {
            del: function (index) {
               
                this.personList.splice(index, 1);




            }
        },
        created() {
            eventBus.$on("personAdded", (person) => {
               
                    this.personList.push(person);
                   

            
        });
        }

    }
</script>