<template>
	<div class="users">
		<h1 :style="{textAlign: 'center', fontSize:'60px'}">My Kitty cats</h1>
		<div class="wrapperDiv">
			<div v-for="(user, idx) in users" :key="idx" class="user">
				<div class="singleUser">
					<div class="userInfo">
						<p>
							Name: <span>{{ user.firstName }}</span>
						</p>
						<p>
							Last Name: <span>{{ user.lastName }}</span>
						</p>
						<hr :style="{margin:'5px 0'}" />
                        <p>Birth date:&nbsp;{{user.birthDate}}</p>
                        <p>Age:&nbsp;{{user.age}}</p>
                        <p>Gender:&nbsp;{{user.gender}}</p>
                        <p>Height:&nbsp;{{user.height}}</p>
                        <p>Weight:&nbsp;{{user.weight}}</p>
                        <p>Number:&nbsp;{{user.phone}}</p>
                        <p>Mail:&nbsp;{{user.email}}</p>
                        <p>Password:&nbsp;{{user.password}}</p>
					</div>
					<div class="img">
						<img :src="user.image" alt="image" />
					</div>
				</div>
			</div>
		</div>
	</div>
</template>


//JS
<script setup>
	import { ref, onMounted } from "vue";

	const users = ref([]);

	onMounted(() => {
		fetch("https://dummyjson.com/users")
			.then((res) => res.json())
			.then((usr) => {
				users.value = usr.users;
				console.log(usr);
			});
	});
</script>


//CSS
<style scoped>
	.users {
		display: flex;
        gap: 3rem;
        flex-direction: column;
		padding: 2rem;
	}
    .wrapperDiv {
        display: flex;
        gap: 15px;
		flex-wrap: wrap;
    }
	.user {
        box-shadow: 1px 2px 14px rgba(0, 0, 0, .1);
		padding: 1rem;
		width: calc(33% - 30px);
		border-radius: 14px;
	}
	.userInfo {
		flex: 65%;
	}
	.userInfo > p > span {
		font-size: 1.4rem;
		color: rgb(158, 150, 66);
	}
	.singleUser {
		display: flex;
		justify-content: space-between;
        align-items: center;
	}
	.img {
		flex: 35%;
		text-align: end;
	}
	.singleUser .img img {
		width: 89px;
	}
</style>