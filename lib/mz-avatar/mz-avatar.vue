<template>
	<view class="">
		<image class='avatar' :src='avatar' :style='{width:`${size}upx`,height:`${size}upx`}'></image>
	</view>
</template>

<script>
	export default{
		name:'MzAvatar',
		props:{
			size:{
				type:Number,
				default:24
			}
		}
	}
</script>

<style>
	.avatar{
		border: 50%;
	}
</style>
