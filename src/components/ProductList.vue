<template>
    
    <div>
        <h2>lol</h2>
        <table class="table is-striped is-bordered mt-2 is-fullwidth">
            <thead>
                <tr>
                  <th>Images</th>
                </tr>
            </thead>
            <tbody>
                <div v-for="item in items" :key="item.id">
                    <img v-bind:src="'data:image/jpeg;base64,'+item.base64" />
                    <p>{{item.id}}</p>
                    <p>{{item.FirstName}}</p>
                    <p>{{item.LastName}}</p>
                    <p>{{item.Gender}}</p>
                    <p>{{item.Adress}}</p>
                    <p>{{item.PhoneNumber}}</p>
                </div>
            </tbody>
        </table>
    </div>
</template>

<script>
// import axios
import axios from "axios";
  
export default {
    name: "ProductList",
    data() {
        return {
            items: [],
        };
    },
  
    created() {
        this.getProducts();
        setInterval(this.getProducts, 1000)
    },
  
    methods: {
        // Get All Products
        async getProducts() {
            try {
                const response = await axios.get("http://localhost:5000/persons");
                this.items = response.data;
            } catch (err) {
                console.log(err);
            }
        },

    },
};
</script>