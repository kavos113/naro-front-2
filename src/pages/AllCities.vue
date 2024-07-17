<script setup lang="ts">
import { ref, onMounted } from 'vue'
const cities = ref()
onMounted(async () => {
    const res = await fetch('/api/allcities')
    if (res.ok) {
        cities.value = await res.json()
    }
})
</script>

<template>
    <h1>City List</h1>
    <table border="1">
        <tr>
            <th>name</th>
            <th>countryCode</th>
            <th>district</th>
            <th>population</th>
        </tr>
        <tr v-for="city in cities" :key="city.name">
            <td><router-link :to="`/city/${city.name.String}`">{{ city.name.String }}</router-link></td>
            <td>{{ city.countryCode.String }}</td>
            <td>{{ city.district.String }}</td>
            <td>{{ city.population.Int64 }}</td>
        </tr>
    </table>
</template>

<!--name, countryCode, district, population-->