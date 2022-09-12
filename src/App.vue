<template>
	<el-container>
		<!-- <el-Header>
			<MyHeader />
		</el-Header>-->
		<el-container class="main">
			<MyAside />
			<router-view></router-view>
		</el-container>
		<el-footer class="footer">
			<MyFooter />
		</el-footer>
	</el-container>
</template>

<script>
// import MyHeader from './components/MyHeader.vue'
import MyAside from './components/MyAside.vue'
import MyFooter from './components/MyFooter.vue'
export default {
	name: 'App',
	components: {
		// MyHeader,
		MyAside,
		MyFooter,
	},
}
</script>

<style>
* {
	margin: 0;
	padding: 0;
}
el-container {
	width: 100%;
}

.footer {
	position: absolute;
	bottom: 20px;
	width: 100%;
}
.main {
	position: absolute;
	width: 100%;
}
</style>
