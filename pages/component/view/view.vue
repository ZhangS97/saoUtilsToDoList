<template>
	<view>
		<view class="uni-flex uni-row">
			<view class="uni-form-item uni-column">
				<view class="uni-input-wrapper">
					<input class="uni-input" focus placeholder="自动获得焦点" confirm-type="search" @confirm="doAdd" />
				</view>
			</view>
		</view>

		<view v-for="todo in todolist" v-bind:key="todo.id">
			<view class="uni-flex uni-row" style="height: 200rpx;">
				<view class="text" style="width: 400rpx;">
					{{todo.name}}
				</view>

				<view class="uni-flex uni-row " style="-webkit-flex: 1;flex: 1;">
					<view class="but" style="-webkit-flex: 1;flex: 1;">
						<button type="primary">完成</button>
					</view>
					<view class="but" style="-webkit-flex: 1;flex: 1;">
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
					id: 0,
					name: 1
				}, {
					id: 1,
					name: 2
				}]
			}
		},
		methods:{
			doAdd: function(event) {    			
				var todo={};
				todo.id = this.todolist.length;
				todo.name = event.detail.value;
				this.todolist.push(todo);
            },
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
	
	.but {
		margin: 15rpx 10rpx;
		padding: 15rpx 20rpx;
		height: 70rpx;
		line-height: 70rpx;
		text-align: center;
		color: #777;
		font-size: 26rpx;
	}

</style>
