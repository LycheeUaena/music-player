<template>
	<el-col>
		<el-row>
			<vue-slider :lazy="true"></vue-slider>
		</el-row>
		<el-row>
			<!-- 信息区 -->
			<el-col :span="4" type="flex">
				<div class="album-pic"></div>
				<!-- <strong>{{musicName}}</strong> -->
			</el-col>
			<!-- 播放器控制、进度条 -->
			<el-col :span="16" type="flex" justify="center">
				<div class="btn-center">
					<el-button type="primary" icon="el-icon-caret-left" circle @click="handlePreNext(-1)"></el-button>
					<el-button
						type="primary"
						:icon="isPlaying? 'el-icon-video-pause': 'el-icon-video-play'"
						@click="handlePlaying"
						circle
					></el-button>
					<el-button type="primary" icon="el-icon-caret-right" circle @click="handlePreNext(1)"></el-button>
				</div>
			</el-col>
			<!-- 音质、音量、播放列表 -->
			<el-col :span="4" type="flex">
				<div class="btn-center">
					<el-button icon="el-icon-caret-left" circle></el-button>
					<el-button icon="el-icon-caret-left" circle></el-button>
					<el-button icon="el-icon-caret-left" circle></el-button>
				</div>
			</el-col>
		</el-row>
	</el-col>
</template>
<script>
import { mapActions, mapGetters } from 'vuex'

import VueSlider from 'vue-slider-component'
import 'vue-slider-component/theme/default.css'
export default {
	components: {
		VueSlider,
	},
	computed: {
		...mapGetters(['isPlaying', 'index', 'localSongs', 'playingSongs']),
		musicName() {
			// 当前播放音乐的名字
			if (this.playingSongs.length === 0) return '未知'
			return this.playingSongs[this.index].name
		},
	},
	methods: {
		...mapActions(['handlePlaying', 'handleClickSong']),
		handlePreNext(step) {
			const index = this.index + step
			if (index >= 0 && index < this.playingSongs.length) {
				this.handleClickSong({
					index,
					audio: this.playingSongs[index].audio,
					name: this.playingSongs[this.index].name,
				})
			}
		},
	},
}
</script>
<style>
.el-button,
.el-button--primary,
.is-circle {
	font-size: 1em;
}
.el-row {
	padding: 0;
}
.album-pic {
	display: inline-block;
	height: 50px;
	width: 50px;
}
.btn-center {
	text-align: center;
}
</style>