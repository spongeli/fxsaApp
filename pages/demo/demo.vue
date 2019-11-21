<template>
	<view>
		<view v-for="(item,index) in list1" :key="index">
			{{index}} - {{item}}
		</view>
		<view class="line"></view>
		<view v-for="(item,index) in list2" :key="index +'ss'">
			{{index}} - {{item.name}} - {{item.age}}
		</view>
		<view class="line"></view>
		<block v-for="(val,key) in objList" :key="key">
			<view>{{key}} -- {{val}}</view>
		</block>
		<view class="line"></view>

		<view class="out" @tap="clickEventOut()">
			<view class="in" @tap.stop="clickEventIn()">
				点击
			</view>
		</view>
		<view class="line"></view>
		<view>{{num}}</view>
		<button type="primary" @tap="changNum()">改变</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list1: ['篮球', '足球', '羽毛球'],
				list2: [{
					"name": "张三",
					"age": 18
				}, {
					"name": "李四",
					"age": 19
				}, {
					"name": "王五",
					"age": 50
				}],
				objList: {
					"name": "李超",
					"age": 13,
					"sex": "男"
				},
				num: 0,
			}
		},
		watch: {
			num: function(val) {
				console.log(val);
			}
		},
		methods: {
			clickEventOut: function() {
				console.log("out");
			},
			clickEventIn: function() {
				console.log("in");
			},
			changNum: function() {
				this.num += 1;
			}
		}
	}
</script>

<style>
	.line {
		width: 750upx;
		border: 1px solid #333333;
	}

	.out {
		width: 360upx;
		height: 360upx;
		padding: 80upx;
		background-color: red;
	}

	,
	.in {
		width: 200upx;
		height: 200upx;
		text-align: center;
		line-height: 200upx;
		background-color: #0A98D5;
	}
</style>
