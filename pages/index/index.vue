<template>
	<view class="content">
		<!-- <image class="logo" src="/static/logo.png"></image> -->
		<van-sidebar v-model="active" @change="onChange">
			<van-sidebar-item title="CPU" />
			<van-sidebar-item title="主板" />
			<van-sidebar-item title="内存" />
			<van-sidebar-item title="显卡" />
			<van-sidebar-item title="固体硬盘" />
			<van-sidebar-item title="机械硬盘" />
			<van-sidebar-item title="电源" />
			<van-sidebar-item title="机箱" />
		</van-sidebar>
		<view class="list-area">
			<view v-for="item in list" style="width: 100%;border-bottom: 1px solid #ccc;padding: 5px 10px;display: flex;">
				<image class="logo" :src="setImg(item.type)"></image>
				<view>
					<view style="display: flex;">
						<view style="display: flex;margin-left: 5px;">
							<view v-if="item.brand">{{ item.brand }}</view>
							<view v-if="item.brandZh">{{ item.brandZh }}</view>
							<view style="margin-left: 5px;    text-overflow: ellipsis;
    overflow: hidden;
    word-break: break-all;
    white-space: nowrap;">{{ item.name }}</view>
						</view>
					</view>
					<view v-if="item.type == 'cpu'" style="margin-left: 5px;">
						<van-tag v-if="item.coresNumber" plain type="primary">{{ item.coresNumber }}核</van-tag>
						<van-tag v-if="item.threadNumber" plain type="primary" style="margin-left: 5px;">{{ item.threadNumber
							}}线程</van-tag>
					</view>
					<view v-if="item.type == 'motherBoard'" style="margin-left: 5px;">
						<van-tag plain type="primary">{{ item.cpuType }}</van-tag>
						<van-tag plain type="primary" style="margin-left: 5px;">{{ item.memoryType }}</van-tag>
					</view>
					<view v-if="item.type == 'memory'" style="margin-left: 5px;">
						<van-tag plain type="primary">{{ item.size }}G</van-tag>
					</view>
					<view v-if="item.type == 'gpu'" style="margin-left: 5px;">
						<van-tag plain type="primary">{{ item.size }}G</van-tag>
					</view>
					<view v-if="item.type == 'ssd'" style="margin-left: 5px;">
						<van-tag plain type="primary">{{ item.size }}G</van-tag>
					</view>
					<view v-if="item.type == 'hdd'" style="margin-left: 5px;">
						<van-tag plain type="primary">{{ item.size }}G</van-tag>
					</view>
				</view>
				<!-- <text class="title">{{ title }}</text> -->
			</view>
		</view>
	</view>
</template>

<script>
import {
	cpuList, boardList, memoryList, gpuList, ssdList, hddList, powerList
} from './index.js'
export default {
	data() {
		return {
			title: 'Hello',
			active: 0,
			cpuList: cpuList,
			boardList: boardList,
			memoryList: memoryList,
			gpuList: gpuList,
			ssdList: ssdList,
			hddList: hddList,
			powerList: powerList,
			list: []
		}
	},
	onLoad() {

	},
	created() {
		this.list = this.cpuList
	},
	methods: {
		onChange(current) {
			const {
				detail
			} = current
			if (detail === 0) {
				console.log("🚀 ~ onChange ~ detail:", detail)
				this.list = this.cpuList
			} else if (detail === 1) {
				console.log("🚀 ~ onChange ~ detail:", detail)
				this.list = this.boardList
			} else if (detail === 2) {
				console.log("🚀 ~ onChange ~ detail:", detail)
				this.list = this.memoryList
			} else if (detail === 3) {
				console.log("🚀 ~ onChange ~ detail:", detail)
				this.list = this.gpuList
			} else if (detail === 4) {
				console.log("🚀 ~ onChange ~ detail:", detail)
				this.list = this.ssdList
			} else if (detail === 5) {
				console.log("🚀 ~ onChange ~ detail:", detail)
				this.list = this.hddList
			} else if (detail === 6) {
				console.log("🚀 ~ onChange ~ detail:", detail)
				this.list = this.powerList
			}
		},
		setImg(type) {
			return '/static/image/' + type + '.png'
		}
	}
}
</script>

<style>
.content {
	display: flex;
	/* flex-direction: column; */
	/* align-items: center; */
	/* justify-content: center; */
}

.logo {
	width: 100rpx;
	height: 100rpx;
}

.list-area {
	width: 100%;
	display: flex;
	/* justify-content: center; */
	flex-direction: column;
}

.title {
	font-size: 36rpx;
	color: #8f8f94;
}
</style>