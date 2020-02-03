<template>
	<view class="barrage">
		<block v-for="(item,index) in items" :key="index">
			<view class="barrage-item" :style="{top: `${item.top}%`,animation: `mymove ${Number(time)}s linear forwards`
				  }">
				<image class='barrage-avatar' :src='item.avatar'></image>
				<text v-if="item.display" class="barrage-text">
					{{item.text}}
				</text>
			</view>
		</block>
	</view>
</template>

<script>
	let cycle;

	export default {
		name: 'MzBarrage',
		props: {
			time:{
				type:Number,
				default:5
			},
			minTop: {
				type: Number,
				default: 0
			},
			maxTop: {
				type: Number,
				default: 300
			}
		},
		data() {
			return {
				items: [],
			}
		},
		methods: {
			add(text = '', time = 5) {
				this.items.push({
					text,
					time,
					top: Math.ceil(Math.random() * (this.maxTop - this.minTop + 1) + this.minTop),
					display: 1,
				});
			},
			start(items = []) {
				this.items = [];
				cycle && (clearInterval(cycle));
				let i = 0,
					len = items.length;

				cycle = setInterval(() => {
					let time = 5;
					if (i < len) {
						this.add(items[i], time);
						i++;
					} else {
						clearInterval(cycle);
						setTimeout(() => {
							this.$emit("end", {});
						}, time * 1000)
					}
				}, 500)
			}
		}
	}
</script>

<style>
	.barrage {
		z-index: 3;
		width: 100%;
		position: fixed;

	}

	.barrage-item {
		background-color: #FFFFFF;
		border-radius: 15px;
		animation: mymove 5s linear forwards;
		animation-timing-function: linear;
		-webkit-animation-timing-function: linear;
		animation-fill-mode: forwards;
	}

	.barrage-avatar {
		width: 15px;
		height: 15px;
		width: 50%;
	}

	.barrage-text {
		position: fixed;
		white-space: nowrap;
	}

	@keyframes mymove {
		from {
			left: 100%;
		}

		to {
			left: -200%;
		}
	}

	@-moz-keyframes mymove

	/* Firefox */
		{
		from {
			left: 100%;
		}

		to {
			left: -200%;
		}
	}

	@-webkit-keyframes mymove

	/* Safari and Chrome */
		{
		from {
			left: 100%;
		}

		to {
			left: -200%;
		}
	}

	@-o-keyframes mymove

	/* Opera */
		{
		from {
			left: 100%;
		}

		to {
			left: -200%;
		}
	}
</style>
