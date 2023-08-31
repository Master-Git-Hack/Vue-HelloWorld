<template>
    <ul>
        <ul v-for="user in users" :key="user.id">
        <li>
            <h3>{{ user.name }}</h3>
            <p>{{ user.email }}</p>
        </li>
        </ul>
        
    </ul>
</template>
<script>
import axios from "axios"
export default {
    data() {
        return {
            users: []
      }  
    },
    mounted() {
        axios.get("https://jsonplaceholder.typicode.com/users")
            .then((response) => this.users = response.data)
            .catch((error) => {
                console.log(error)
            })
    }
}
</script>