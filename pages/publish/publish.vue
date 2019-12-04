<template>
	<view>
		<view class="status_bar"><!-- 这里是状态栏 --></view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar left-icon="arrowleft" @clickRight="publish" @clickLeft="back" rightText="发布">
			<view class="v-fjc" style="margin: 0 auto;" @tap="selectVisible">
				{{title}}
				<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
		<!-- 文本域 -->
		<view class="uni-textarea">
			<textarea v-model="content" placeholder="写点东西吧~" />
		</view>
		<!-- 图片上传 -->
		<upload-img @changeImgs="changeImgs"></upload-img>
		<!-- 提示框 -->
		<model-frame :show="showModel">
			<view class="model-frame-back">
				<image src="../../static/common/native.jpg" mode="widthFix"></image>
				 <view class="model-frame-back-context">
					 <view>1.涉及黄色、政治、广告和骚扰的信息</view>
					 <view>1.涉及黄色、政治、广告和骚扰的信息</view>
					 <view>1.涉及黄色、政治、广告和骚扰的信息</view>
					 <view>1.涉及黄色、政治、广告和骚扰的信息</view>
				 </view>
				 <button type="primary" @tap="close">朕知道了</button>
			</view>
		</model-frame>
	</view>
</template>

<script>
	let itemList = ['所有人可见', '仅自己可见'];
	import uploadImg from "../../components/common/upload-img.vue";
	import modelFrame from "../../components/common/model_frame.vue";
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";
	export default {
		components: {
			uniNavBar,
			uploadImg,
			modelFrame
		},
		data() {
			return {
				title: "所有人可见",
				imageList:[],
				showModel:true,
				content:""
			}
		},
		methods: {
			close(){
				this.showModel = false;
			},
			// 返回时提示
			back() {
				if(this.content || this.imageList.length > 0){
					uni.showModal({
						cancelColor:"不保存",
						confirmText:"保存",
						title:"是否保存编辑",
						success(res) {
							if(confirm){
								console.log("保存编辑");
							}
							uni.navigateBack({
								delta: 1
							});
						}
					});
				}else{
					uni.navigateBack({
						delta: 1
					});
				}
			},
			publish() {
				console.log("发布");
			},
			// 选择可见选项
			selectVisible() {
				uni.showActionSheet({
					itemList: itemList,
					success: (res) => {
						this.title = itemList[res.tapIndex];
					},
					fail: (res) => {
						console.log(res.errMsg);
					}
				});
			},
			changeImgs(arr){
				this.imageList = arr;
			}
		}
	}
</script>

<style>	
	.status_bar{
		height: var(--status-bar-height);
		width: 100%;
	}
	
	.model-frame-back{
		width: 650upx;
		text-align: center;
		background-color: #FFFFFF;
		border-radius: 14upx;
	}
	.model-frame-back image{
		width: 350upx;
	}
	.model-frame-back-context{
		width: 600upx;
		margin: 0 auto;
	}
	.model-frame-back-context>view{
		font-size: 35upx;
		color: #131313;
		margin-top: 15upx;
	}
	.model-frame-back>button{
		color: #000000;
		background-color: #FFE934;
		width: 600upx;
		margin: 15upx auto;
	}
	
	
	.uni-textarea{
		border: 1upx solid #F4F4F4;
	}
	.cell-pd {
		padding: 22upx 26upx;
	}
	
	.list-pd {
		margin-top: 50upx;
	}
</style>
