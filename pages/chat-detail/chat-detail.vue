<template>
	<view>
		<text-uni-nav-bar leftIcon="icon-fanhui" rightIcon="icon-geren" :centerText="chatDetailInfo.userNickName" 
				@leftClick="leftClick" @rightClick="rightClick"></text-uni-nav-bar>
	</view>
</template>

<script>
	import textUniNavBar from "../../components/common/text-uni-nav-bar.vue";
	export default {
		components: {
			textUniNavBar
		},
		data() {
			return {
				chatDetailInfo: {
					userNickName: "JAVA大亨"
				}
			}
		},
		methods: {
			leftClick(){
				uni.navigateBack({
					delta:1,
					animationType: 'pop-out',
					animationDuration: 200
				})
			},
			rightClick(){
				uni.navigateTo({
					url:"../user-info/user-info"
				});
			}
		}
	}
</script>

<style>

</style>
