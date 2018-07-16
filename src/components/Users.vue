<template>
	<div id="users">
		<h1>Users</h1>
		<form v-on:submit="addUser">
			<input type="text" v-model="newUsers.name" placeholder="enter name">
			<input type="text" v-model="newUsers.email" placeholder="enter email">
			<input type="submit" value="Add User">
		</form>
		<ul>
			<li><input type="checkbox">姓名 -- 邮箱</li>
			<li v-for="user in users">
				<input type="checkbox" v-on:click="user.contacted=!user.contacted">
				<span v-bind:class="{contacted:user.contacted}">
					{{user.name}} -- {{user.email}}
					<input type="button" v-on:click="deleteUser(user)" value="delete user">
				</span>
				
			</li>
		</ul>
		<input type="button" v-on:click="deleteUsers()" value="delete users">
	</div>
</template>

<script>
	export default{
		name:"users",
		data(){
			return {
				newUsers:{},
				users:[
					{
						name:"Henry",
						email:"henry@qq.com",
						contacted:false
					},
					{
						name:"Lee",
						email:"lee@qq.com",
						contacted:false
					},
					{
						name:"Jay",
						email:"jay@qq.com",
						contacted:false
					}
				]
			}
		},
		methods:{
			addUser:function(e){
				this.users.push({
					name:this.newUsers.name,
					email:this.newUsers.email,
					contacted:false
				});
				e.preventDefault();
			},
			deleteUser:function(user){
				this.users.splice(this.users.indexOf(user),1);
			},
			deleteUsers:function(){
				for(var i=0;i<this.users.length;i++){
					if(this.users[i].contacted){
						this.users.splice(this.users[i],1);
					}
				}
			}
		}
		
	}
</script>

<style scoped>
	ul{
		list-style-type: none;
	}
	.contacted{
		text-decoration:line-through;
	}
</style>