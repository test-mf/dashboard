<template>
	<div class="user" v-if="userInfo">Hello, {{ userInfo.firstName }}</div>
	<div class="user" v-if="!userInfo">LOADING USER INFO</div>
</template>

<script>
import { getUserInfo, isUserLogin } from "@test-mf/api";

export default {
	name: "DashBoard",
	data() {
		return {
			userInfo: null,
		};
	},
	mounted() {
		isUserLogin() || history.pushState(null, null, "#/signIn");
		getUserInfo().then(info => (this.userInfo = info));
	},
};
</script>

<style>
.user {
	display: flex;
	justify-content: center;
	font-size: 2em;
}
</style>
