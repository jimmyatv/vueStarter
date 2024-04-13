<template>
	<div class="workers">
		<div :style="{textAlign:'center', margin:'20px 0'}">
			<h1>Worker list</h1>
			<input v-model="search" type="text" placeholder="Search..." />
			<p>TEST:{{search}}</p>
		</div>
		<div class="workersList"></div>
	</div>
</template>




<script setup>
	import { ref, onMounted } from "vue";

	const search = ref("");
    const workers = ref([]);

    onMounted(async () => {
        try {
            const res = await fetch('https://api.escuelajs.co/api/v1/users')
            const data = await res.json()

            workers.value = data

            console.log(data)
        } catch (error) {
            console.error('Error', error)
        }
    })

    
</script>




<style scoped>
</style>