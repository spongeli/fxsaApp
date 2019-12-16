<template>
	<view>
		<!-- 导航 -->
		<text-uni-nav-bar leftIcon="icon-fanhui" rightIcon="icon-gengduo1" @leftClick="leftClick" @rightClick="rightClick"
		 :centerText="item.title"></text-uni-nav-bar>

		<!-- 内容 -->
		<dynamic-detail-index :item="item" @commonClick="commonClick(0)"></dynamic-detail-index>

		<!-- 最新评论 -->
		<view class="common-context">
			<view>最新评论 1</view>
			<block v-for="(item,index) in commonList" :key="index">
				<uni-comment :item="item" @addCommon="commonClick"></uni-comment>
			</block>
		</view>

		<!-- 分享页面 -->
		<share v-show="false"></share>
		
		<!-- input 组件 -->
		<view class="input-bk" v-show="inputShow" @tap="cancelBk"></view>
		<view style="height: 90upx;" v-show="fuzzyBackground"></view>
		<chat-input :show="inputShow" @submit="submit"></chat-input>
	</view>
</template>

<script>
	import textUniNavBar from "../../components/common/text-uni-nav-bar.vue";
	import dynamicDetailIndex from "../../components/dynamic/dynamic-detail-index.vue";
	import uniComment from "../../components/common/uni-comment.vue";
	import chatInput from "../../components/chat/chat-input.vue";
	import share from "../../components/common/share.vue"
	import time from "../../common/time.js";
	export default {
		components: {
			textUniNavBar,
			dynamicDetailIndex,
			uniComment,
			chatInput,
			share
		},
		data() {
			return {
				item: null,
				commonList: [],
				inputShow: false,
				scrollTop: 0,
				pid: 0,
				fuzzyBackground:false
			}
		},
		onLoad(data) {
			this.onloadInntData(data.messageId);
		},
		onReady() {},
		methods: {
			leftClick() {
				uni.navigateBack({
					delta: 1
				})
			},
			rightClick() {
				console.log("分享");
			},
			onloadInntData(messgaeId) {
				var obj = {
					nickPick: "/static/userpic/14.jpg",
					nickName: "昵称",
					sex: 1, // 性别<>0 = 女  1 = 男
					age: 25,
					isGuanZhu: false,
					title: "动态内容动态内容动态内容动态内容动态内容动态内容",
					mediaType: "image", // 媒体类型<>image=图片&video=视频&share=分享
					mediaSrc: "/static/datapic/15.jpg",
					mediaSrcList: ["/static/datapic/15.jpg", "/static/datapic/16.jpg", "/static/datapic/17.jpg"],
					shareText: "信息信息信息信息信息息信信息信息信息信信息信息息信息信息信息信息息信息信息信息信息信息信息息信信息信息信息信信息信息息信息信息信息信息息信息",
					addressProvince: "甘肃",
					addressCity: "酒泉",
					commentInfo: {
						zhanfaNum: 50,
						pinglunNum: 60,
						dianzanNum: 50
					},
					messageTime: 1573872049
				};

				var arr = [{
						id: 1,
						pid: 0,
						userpic: "/static/userpic/12.jpg",
						nickname: "仰望天空",
						commoncount: 2,
						commontime: 1573872049,
						commontext: "35岁程序员，年薪9999W"
					}, {
						id: 2,
						pid: 1,
						userpic: "/static/userpic/13.jpg",
						nickname: "仰望天空",
						commoncount: 5,
						commontime: 1573872049,
						commontext: "35岁程序员，年薪9999W"
					}, {
						id: 3,
						pid: 1,
						userpic: "/static/userpic/14.jpg",
						nickname: "仰望天空",
						commoncount: 0,
						commontime: 1573872049,
						commontext: "35岁程序员，年薪9999W"
					},
					{
						id: 4,
						pid: 0,
						userpic: "/static/userpic/15.jpg",
						nickname: "仰望天空",
						commoncount: 0,
						commontime: 1573872049,
						commontext: "35岁程序员，年薪9999W"
					}
				]

				this.item = obj;
				this.commonList = arr;
			},
			commonClick(pid) {
				this.pid = pid;
				this.inputShow = true;
				this.fuzzyBackground = true;
			},
			submit(text) {
				this.addCommonSubmit(this.pid, text);
			},
			cancelBk(){
				this.pid = 0;
				this.inputShow = false;
				this.fuzzyBackground = false;
			},
			addCommonSubmit(pid, text) {
				var obj = {
					id: 1,
					pid: pid,
					userpic: "/static/userpic/12.jpg",
					nickname: "仰望天空",
					commoncount: 2,
					commontime: new Date().getTime(),
					commontext: text
				}
				if (pid == 0) {
					this.commonList.push(obj);
				} else {
					var index = 0;
					for (var i = 0; i < this.commonList.length; i++) {
						if (this.commonList[i].pid == pid) {
							index = i;
							break;
						}
					}
					this.commonList.splice(index, 0, obj);
				}
			}
		}
	}
</script>

<style>
	.input-bk{
		position: fixed;
		top: 0;
		left: 0;
		bottom: 0;
		right: 0;
		background-color: rgba(204, 204, 204, 0.23);
		z-index: 999;
	}
	.common-context {
		width: 100%;
		box-sizing: border-box;
		padding: 30upx;
	}

	.common-context>view:first-child {
		font-size: 30upx;
		font-weight: bold;
	}
</style>
