<template>
    <div class="container" id="addStartup">
        <form>
            <div class="row">
                <div class="card p-3">
                    <h5 class="card-title">Startup Details</h5>
                    <div class="card-body">
                        <div class="mb-3">
                            <label for="name" class="form-label">Startup Name</label>
                            <input
                            type="text"
                            class="form-control"
                            id="name"
                            placeholder="Enter Startup Name"
                            autocomplete="off"
                            v-model="name"
                            required />
                        </div>
                        <div class="mb-3">
                            <label for="category" class="form-label">Category</label>
                            <select class="form-select" v-model="selected">
                                <option v-for="option in options" :key="option.id" :value="option.value">
                                    {{ option.value }}
                                </option>
                            </select>
                        </div>
                        <div class="mb-3">
                            <label for="owner" class="form-label">Owner</label>
                            <input
                            type="text"
                            class="form-control"
                            id="owner"
                            placeholder="Enter the owner"
                            autocomplete="off"
                            v-model="owner" 
                            required />
                        </div>
                        <div class="mb-3">
                            <label for="description" class="form-label">Description</label>
                            <textarea class="form-control" rows="3" placeholder="Enter Short Description" v-model="description"></textarea>
                        </div>
                        <div>
                            <button class="btn btn-primary" type="submit" @click="submitForm">Submit</button>
                        </div>
                    </div>
                </div>
            </div>
        </form>
    </div>
  </template>
  
  <script>
  import axios from "axios";
  
  const baseURL = "http://localhost:3000/startups";
  
  export default {
    data: () => ({
        name: '',
        selected: '',
        options: [
            { id: '1', value: 'Health'},
            { id: '2', value: 'Technology'},
            { id: '3', value: 'Education'},
            { id: '4', value: 'Social'},
            { id: '5', value: 'Business'},
        ],
        owner: '',
        description: '',
  
    }),
    async created() {
    try {
        const res = await axios.get(baseURL);
  
        this.startups = res.data;
    } catch (e) {
        console.error(e);
    }
    },
    methods: {
        async submitForm() {
        try {
        const res = await axios.post(baseURL, {
            id: this.id,
            name: this.name,
            category: this.selected,
            owner: this.owner,
            description: this.description,
        });
            this.startups = [...this.startups, res.data];
            this.id = "";
            this.name = "";
            this.category = "";
            this.owner = "";
            this.description = "";
            } catch (e) {
                console.error(e);
            }
            console.log("Name: " + this.name);
            console.log("Category: " + this.selected);
            console.log("Owner: " + this.owner);
            console.log("Description: " + this.description);
        }
            
    }
  }
    
  
  </script>