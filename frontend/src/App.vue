<template>
	<div>
		<h1>Laravel + Vue App</h1>
		<p>Backend Status: {{ status }}</p>
	</div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const status = ref('Checking...')

onMounted(async () => {
	try {
		const response = await axios.get('/api/health')
		status.value = response.data.status
	} catch (error) {
		status.value = 'Error'
		console.error('Failed to fetch health:', error)
	}
})
</script>