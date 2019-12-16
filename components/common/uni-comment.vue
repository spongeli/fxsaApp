<template>
	<view>
		<view class="uni-padding-wrap">
			<!--  
					{
						id: 2,
						pid: 1,
						userpic: "/static/userpic/12.jpg",
						nickname: "仰望天空",
						commoncount: 5,
						commontime: 1573872049,
						commontext: "35岁程序员，年薪9999W"
					}
			-->
			<!-- 评论区 start -->
			<view class="uni-comment" :class="{'uni-comment-children-back':item.pid != 0}">
				<view class="uni-comment-list">
					<view class="uni-comment-face">
						<image :src="item.userpic" mode="widthFix"></image>
					</view>
					<view class="uni-comment-body">
						<view class="uni-comment-top">
							<text>{{item.nickname}}</text>
						</view>
						<view class="uni-comment-content">{{item.commontext}}!</view>
						<view class="uni-comment-date">
							<view>{{ZHCommontime}}</view>
							<view class="uni-comment-replay-btn" v-show="item.commoncount > 0" @tap="addCommon">{{item.commoncount}}回复</view>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import time from "../../common/time.js"
	export default {
		props: {
			item: Object
		},
		data() {
			return {
				itemObj: this.item
			}
		},
		methods: {
			addCommon() {
				this.$emit("addCommon", this.item.id);
			}
		},
		computed: {
			ZHCommontime: function() {
				return time.gettime.getDateDifference(this.itemObj.commontime);
			}
		}
	}
</script>

<style scoped>
	.uni-padding-wrap {
		padding: 0 0;
	}

	.uni-comment-list {
		margin: 0 0;
	}

	.uni-comment-children-back {
		margin-left: 90upx;
		background-color: #F4F4F4;
		box-sizing: border-box;
		padding: 0 10upx;
	}
</style>
