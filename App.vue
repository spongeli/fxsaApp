<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/* 每个页面公共css */
	@import url("./common/uni.css");
	/* 引入第三方标签库 */
	@import url("./common/icon.css");
	/* 引入第三方动画库 */
	@import url("./common/animate.css");
	/* 引入本项目的公共样式 */
	@import url("./common/common.css");
</style>
