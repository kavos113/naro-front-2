<script setup lang="ts">
import { ref, onMounted } from 'vue'
const props = defineProps<{ cityName: string }>()
const cityInfo = ref()
onMounted(async () => {
    const res = await fetch('/api/cities/' + props.cityName)
    if (res.ok){
        cityInfo.value = await res.json()
    }
})
</script>

<template>
    <div>
        <h1>
            {{ cityName }}
        </h1>
        <div v-if="cityInfo">
            <ul>
                <li>name: {{ cityInfo.name.String }}</li>
                <li>countryCode: {{ cityInfo.countryCode.String }}</li>
                <li>district: {{ cityInfo.district.String }}</li>
                <li>population: {{ cityInfo.population.Int64 }}</li>
            </ul>
        </div>
        <div v-else>街が見つかりませんでした</div>
    </div>
</template>