<template>
	<div id="test">
		<h1>{{title}}</h1>
		<p>{{user.firstName}}</p>
		<p v-text="user.lastName"></p>

		<p v-if="showName">{{user.lastName}}</p>
	</div>
</template>

<script>
	export default{
		name:"test",
		data(){
			return {
				title:"Hello Vue.js!",
				user:{
					firstName:"Lucky",
					lastName:"Lee"
				},
				showName:true
			}
		}
	}
</script>

<style scoped>
	
</style>