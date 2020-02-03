<template>
	<view class="tag" :style='{backgroundColor:bgColor}' @click='onClick()'>
		{{tagText}}
	</view>
</template>

<script>
	export default {
		name: 'MzTag',
		props: {
			bgColor: {
				type: String,
				default: '#F0AD4E'
			},
			tagText:{
				type:String,
				default:'活动详情'
			}
		},
		data() {
			return {

			}
		}
		,methods:{
			onClick() {
				this.$emit('click');
			}
		}
	}
</script>

<style>
	.tag {
		color: #FFFFFF;
		border-radius: 10px 0 0 10px;
		margin: 15upx 0;
		width: 80upx;
		height: 32upx;
		font-size: 24upx;
		line-height: 32upx;
		padding-left: 15upx;
	}
</style>
