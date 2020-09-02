<template>
	<view>
		<view class="uni-flex uni-row">
			<view style="width: 400rpx;">
				？？？？？？？？？
			</view>
		</view>

		<view v-for="todo in todolist" v-bind:key="todo.id">
			<view class="uni-flex uni-row">
				<view class="text" style="width: 400rpx;">
					{{todo.name}}
				</view>

				<view class="uni-flex uni-row" style="-webkit-flex: 1;flex: 1;">
					<view style="-webkit-flex: 1;flex: 1;">
						<button type="primary">完成</button>
					</view>
					<view style="-webkit-flex: 1;flex: 1;">
						<button type="warn">取消</button>
					</view>
				</view>
			</view>
		</view>

	</view>
</template>
<script>
	export default {
		data() {
			return {
				todolist: [{
					id: 1,
					name: 1
				}, {
					id: 2,
					name: 2
				}]
			}
		}
	}
</script>

<style>
	.text {
		margin: 15rpx 10rpx;
		padding: 0 20rpx;
		background-color: #ebebeb;
		height: 70rpx;
		line-height: 70rpx;
		text-align: center;
		color: #777;
		font-size: 26rpx;
	}

	.desc {
		/* text-indent: 40rpx; */
	}
</style>
