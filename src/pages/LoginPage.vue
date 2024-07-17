<script setup lang="ts">
import { ref } from 'vue'

const username = ref<string>('')
const password = ref<string>('')

const login = () => {
    fetch('/api/login', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            username : username.value,
            password : password.value
        })
    })
}
</script>

<template>
    <h1>Please Login.</h1>
    <div>
        <label>
            username: 
            <input v-model="username" type="text" />
        </label>
        <label>
            password: 
            <input v-model="password" type="password" />
            <button @click="login">Login</button> 
        </label>
    </div>
    
</template>