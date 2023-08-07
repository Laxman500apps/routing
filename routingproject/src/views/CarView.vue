<script setup>
    import {useRoute, RouterView, useRouter} from 'vue-router'
    import {ref, onBeforeMount} from 'vue'
    import cars from '../data.json'
    
    const router = useRouter()
    const car = ref(null) 
    const route = useRoute() 
    const {id} = route.params 


    onBeforeMount(() => {
        car.value = cars.find(c => c.id === parseInt(id)) 
    })
</script>

<template>
    <div class="container">
        <h1>The Car</h1>
        <p>Make: {{ car.make }}</p>
        <p>Body: {{ car.body}}</p>
        <p>Price: {{ car.price }}</p>
        <p>Year: {{ car.year }}</p>
        <button @click="router.back()">back</button>
        <br />
        <div>
            <button @click="router.push(`/car/${car.id}/dealer`)">dealer details</button>
            <button @click="router.push(`/car/${car.id}/manufacturer`)">manufacturer details</button>
        </div>
        <RouterView />
    </div>
</template>