<template>
	<view class="">
		<u-divider>按照权重计算概率 </u-divider>
		
		1.计算权重的和；Math.random() * 权重和 为随机值 
		2.将随机值放入数组，从小到大排序（sort）,找到随机值对应的下标 ；且下标不大于（数组长度-1） 
		3.原数组的 this.list[randomIndex] 为抽中的奖项 
		
		<u-divider>动画创建的代码 </u-divider>
		var animationRun = uni.createAnimation({
			 duration: duration,
			 timingFunction: 'ease' 
		}) 
		animationRun.rotate(this.runDeg).step(); 
		this.animationData = animationRun.export(); 
	</view>
</template>

<script>
</script>

<style>
</style>
