<template>
	<view>
		<!-- 自定义导航 -->
		<view class="status_bar">
			<!-- 这里是状态栏 -->
		</view>
		<uni-nav-bar>
			<!-- 左边 -->
			<block slot="left">
				<view class="icon iconfont icon-qiandao left-icon"></view>
			</block>
			<block>
				<view class="center-icon">
					<block v-for="(item,index) in tabBers" :key="index">
						<view @tap="changtabIndex(index)" :class="{'active':index==tabBerIndex}">{{item.name}}</view>
					</block>
				</view>
			</block>
			<block slot="right">
				<view class="right-icon" @tap="toPublish">
					<view class="icon iconfont icon-bianji1"></view>
				</view>
			</block>
		</uni-nav-bar>


		<!-- 动态内容 -->
		<block v-for="(item,index) in dynamicInfos" :key="index">
			<dynamic-list :item="item"></dynamic-list>
		</block>
	</view>
</template>

<script>
	import uniNavBar from "../../../components/uni-nav-bar/uni-nav-bar.vue";
	import dynamicList from "../../../components/dynamic/dynamic-list.vue";
	export default {
		components: {
			uniNavBar,
			dynamicList
		},
		data() {
			return {
				tabBerIndex: 0,
				tabBers: [{
					name: "关注",
					id: "guanzhu"
				}, {
					name: "话题",
					id: "huati"
				}],
				// 动态信息
				dynamicInfos: [{
						nickPick: "/static/userpic/14.jpg",
						nickName: "昵称",
						sex: 1, // 性别<>0 = 女  1 = 男
						age: 25,
						isGuanZhu: true,
						title: "动态内容动态内容动态内容动态内容动态内容动态内容",
						mediaType: "video", // 媒体类型<>image=图片&video=视频
						mediaSrc: "/static/datapic/15.jpg",
						videoInfo: {
							playNum: "50W",
							playTime: "2:45",
						},
						addressProvince: "甘肃",
						addressCity: "酒泉",
						commentInfo: {
							zhanfaNum: 50,
							pinglunNum: 60,
							dianzanNum: 50
						}
					},
					{
						nickPick: "/static/userpic/14.jpg",
						nickName: "昵称",
						sex: 0, // 性别<>0 = 女  1 = 男
						age: 25,
						isGuanZhu: false,
						title: "动态内容动态内容动态内容动态内容动态内容动态内容",
						mediaType: "image", // 媒体类型<>image=图片&video=视频
						mediaSrc: "/static/datapic/15.jpg",
						videoInfo: {
							playNum: "50W",
							playTime: "2:45",
						},
						addressProvince: "甘肃",
						addressCity: "酒泉",
						commentInfo: {
							zhanfaNum: 50,
							pinglunNum: 60,
							dianzanNum: 50
						}
					},
					{
						nickPick: "/static/userpic/14.jpg",
						nickName: "昵称",
						sex: 1, // 性别<>0 = 女  1 = 男
						age: 25,
						isGuanZhu: false,
						title: "动态内容动态内容动态内容动态内容动态内容动态内容",
						mediaType: "video", // 媒体类型<>image=图片&video=视频
						mediaSrc: "/static/datapic/15.jpg",
						videoInfo: {
							playNum: "50W",
							playTime: "2:45",
						},
						addressProvince: "甘肃",
						addressCity: "酒泉",
						commentInfo: {
							zhanfaNum: 50,
							pinglunNum: 60,
							dianzanNum: 50
						}
					}
				]
			}
		},
		methods: {
			// 切换话题
			changtabIndex(index) {
				this.tabBerIndex = index;
			},
			toPublish() {
				uni.navigateTo({
					url: "../../publish/publish"
				})
			}
		}
	}
</script>

<style>
	.status_bar {
		height: var(--status-bar-height);
		width: 100%;
	}

	/* 导航栏样式 start */
	.left-icon {
		font-size: 40upx;
		color: #FF9B25;
	}

	.right-icon {
		width: 100%;
		text-align: right;
	}

	.right-icon>view {
		font-size: 40upx;
		font-weight: bold;
	}

	.center-icon {
		width: 100%;
		display: flex;
		justify-content: center;
	}

	.center-icon>view {
		color: #969696;
		font-size: 35upx;
		font-weight: bold;
	}

	.center-icon>view:first-child {
		margin-right: 20upx;
	}

	.center-icon .active {
		color: #343434;
		border-bottom: 8upx solid #FEDE33;
	}

	/* 导航栏样式 end */
</style>
