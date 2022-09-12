<template>
	<!-- 侧边栏容器 -->
	<el-aside>
		<el-radio-group v-model="isCollapse" style="margin-bottom: 20px;">
			<!-- label: Radio的value(string/number) -->
			<el-radio-button :label="false">展开</el-radio-button>
			<el-radio-button :label="true">收起</el-radio-button>
		</el-radio-group>
		<!-- collapse: 是否水平折叠收起菜单 -->
		<!-- default-active: 当前激活菜单的index -->
		<el-menu class="el-menu-vertical" :collapse="isCollapse" default-active="1">
			<el-menu-item index="1" @click="jumpTo(1)">
				<i class="el-icon-headset"></i>
				&nbsp;&nbsp;
				<span slot="title">本地音乐</span>
			</el-menu-item>
			<el-menu-item index="2" @click="jumpTo(2)">
				<i class="el-icon-s-unfold"></i>
				&nbsp;&nbsp;
				<span slot="title">播放列表</span>
			</el-menu-item>
			<el-menu-item index="3" @click="jumpTo(3)">
				<i class="el-icon-time"></i>
				&nbsp;&nbsp;
				<span slot="title">最近播放</span>
			</el-menu-item>
		</el-menu>
	</el-aside>
</template>
<script>
export default {
	data() {
		return {
			isCollapse: false,
		}
	},
	methods: {
		jumpTo(index) {
			const targetRoute =
				index === 1
					? '/localmusic'
					: index === 2
					? '/playingmusic'
					: '/playedmusic'
			if (this.$route.path !== targetRoute) {
				this.$router.replace(targetRoute)
			}
		},
	},
}
</script>
<style>
</style>