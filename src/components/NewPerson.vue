<template>
    <div class="row">
        <div class="card offset-2 col-md-3">
            <div class="card-body tex-center d-flex align-items-center flex-column">
                <img height="128" class="img-responsive text-center mb-3"
                     :src="person.selectedImage == null ? './default.png' : person.selectedImage">
                <input ref="file" type="file" style="display: none;" @change="onChange($event)" class="form-control">
                <button class="btn btn-outline-secondary " type="button" @click="$refs.file.click()">Profile picture</button>
            </div>
        </div>
        <div class="col-md-5">
            <div class="col-md-11 card">
                <div class="card-body">
                    <div class="form-group">
                        <label>Person Name</label>
                        <input type="text" v-model="person.name" class="form-control" placeholder="name..">
                    </div>
                    <div class="row">
                        <div class="form-group col-md-6">
                            <label>Birt of Year</label>
                            <input type="text" v-model="person.birth" class="form-control"
                                   placeholder="birth of year...">
                        </div>
                        <div class="form-group col-md-6">
                            <label>City </label>
                            <input type="text" v-model="person.city" class="form-control"
                                   placeholder="City...">
                        </div>
                        
                    </div>
                    <button @click="addPerson" class="btn btn-outline-info btn-block">Register</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import {eventBus} from "../main";

    export default {
        data() {
            return {
                person: {
                    name: null,
                    city: null,
                    birth: null,
                    selectedImage: null
                }
            }
        },
        methods: {
            onChange(e) {
                const file = e.target.files[0];
                this.person.selectedImage = URL.createObjectURL(file);
            },
            addPerson() {
                
                
                
                eventBus.$emit("personAdded", this.person);
                this.person = {
                    name: null,
                    city: null,
                    birth: null,
                    selectedImage: null
                }
            }
        }
    }
</script>