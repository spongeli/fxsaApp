<template>
	<view class="char-list-span v-fjs" @tap="toChatDetail">
		<image :src="item.userpic" mode="widthFix"></image>
		<view>
			<view class="char-list-span1 v-fjs">
				<view>{{item.usernick}}</view>
				<view>{{item.chatTime}}</view>
			</view>
			<view class="char-list-span2 v-fjs">
				<view>{{ZHchatText}}</view>
				<view>
					<uni-badge :text="item.unReaderNum" type="error" />
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniBadge from "../uni-badge/uni-badge.vue";
	export default {
		components: {
			uniBadge
		},
		props: {
			chatInfo: Object
		},
		data() {
			return {
				item: this.chatInfo
			}
		},
		computed: {
			ZHchatText: function() {
				var charText = this.chatInfo.chatText;
				return charText.length <= 15 ? charText : (charText.substring(0, 15) + "...");
			}
		},
		methods:{
			toChatDetail(){
				uni.navigateTo({
					url:"/pages/chat-detail/chat-detail"
				})
			}
		}
	}
</script>

<style>
	
	/* 聊天列表 start */
	.char-list-span {
		width: 716upx;
		height: 150upx;
		margin: 0 auto;
		padding: 15upx 0;
		border-bottom: 3upx solid #EEEEEE;
	}
	
	.char-list-span>view:last-child {
		width: 100%;
		margin-left: 15upx;
	}
	
	.char-list-span image {
		width: 130upx;
		border-radius: 100%;
	}
	
	.char-list-span1 {
		padding-top: 10upx;
	}
	.char-list-span1>view:first-child{
		font-size: 35upx;
		color: #010101;
	}
	.char-list-span1>view:last-child{
		font-size: 25upx;
		color: #CBCBCB;
	}
	.char-list-span2 {
		padding-top: 10upx;
	}
	.char-list-span2>view:first-child {
		color: #9A9A9A;
		font-size: 30upx;
	}
	/* 聊天列表 end */
</style>
