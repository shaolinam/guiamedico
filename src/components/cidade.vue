<template>
	<div>
		<div v-for="cidade in items" :key="cidade">
	        <p>{{cidade}}</p>
	    </div>
	</div>
</template>

<script>
	export default {
		props: ["items"]
	}
</script>