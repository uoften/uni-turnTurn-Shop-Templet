<template>
	<view class="zaiui-news-box" :class="show?'show':''">
		<!--标题栏-->
		<bar-title bgColor="bg-white" :isBack="false" @rightTap="barTitleRightTap">
			<block slot="content">消息中心</block>
			
			<!--小程序端不显示-->
			<!-- #ifndef MP -->
			<block slot="right">
				<text class="cuIcon-info"></text>
			</block>
			<!-- #endif -->
			
		</bar-title>
		
		<!--关注-->
		<view class="cu-bar bg-white zaiui-follow-box">
			<view class="action action-text-cut">
				<view class="text-cut-2 text-sm">
					关注微信公众号,通过微信随时接收用户咨询、订单状态
				</view>
			</view>
			<view class="action">
				<button class="cu-btn sm bg-red">立即关注</button>
			</view>
		</view>
		
		<!--宫格菜单-->
		<view class="margin-bottom zaiui-grid-menu">
			<view class="bg-white cu-list grid col-3 no-border">
				<view class="cu-item">
					<!-- #ifndef MP-TOUTIAO -->
					<view class="cu-avatar lg round" style="background-image:url(../../static/images/news/1.png);"/>
					<!-- #endif -->
					
					<!-- #ifdef MP-TOUTIAO -->
					<view class="cu-avatar lg round" style="background-image:url(static/images/news/1.png);"/>
					<!-- #endif -->
					<view class="margin-top-sm text-sm">交易信息</view>
				</view>
				<view class="cu-item">
					<!-- #ifndef MP-TOUTIAO -->
					<view class="cu-avatar lg round" style="background-image:url(../../static/images/news/2.png);"/>
					<!-- #endif -->
					
					<!-- #ifdef MP-TOUTIAO -->
					<view class="cu-avatar lg round" style="background-image:url(static/images/news/2.png);"/>
					<!-- #endif -->
					<view class="margin-top-sm text-sm">留言信息</view>
				</view>
				<view class="cu-item">
					<!-- #ifndef MP-TOUTIAO -->
					<view class="cu-avatar lg round" style="background-image:url(../../static/images/news/3.png);"/>
					<!-- #endif -->
					
					<!-- #ifdef MP-TOUTIAO -->
					<view class="cu-avatar lg round" style="background-image:url(static/images/news/3.png);"/>
					<!-- #endif -->
					<view class="margin-top-sm text-sm">互动信息</view>
				</view>
			</view>
		</view>
		
		<!--消息列表-->
		<view class="bg-white zaiui-news-list-box">
			<view class="margin-bottom cu-list menu-avatar">
				
				<view class="cu-item" :class="modalName=='move-box-'+ 0?'move-cur':''" @touchstart="ListTouchStart" @touchmove="ListTouchMove"
				 @touchend="ListTouchEnd" :data-target="'move-box-' + 0" @tap="tapNews(0)">
					<!-- #ifndef MP-TOUTIAO -->
					<view class="cu-avatar round" style="background-image:url(../../static/images/news/4.png);">
						<view class="cu-tag badge"/>
					</view>
					<!-- #endif -->
					 
					<!-- #ifdef MP-TOUTIAO -->
					<view class="cu-avatar round" style="background-image:url(static/images/news/4.png);">
						<view class="cu-tag badge"/>
					</view>
					<!-- #endif -->
					<view class="content">
						<view class="text-black">通知助手</view>
						<view class="text-gray text-sm text-cut">小米:“我忍你很久了!”</view>
						<view class="text-gray text-sm">3小时前</view>
					</view>
					<view class="move">
						<view class="bg-grey">置顶</view>
						<view class="bg-red">删除</view>
					</view>
				</view>
				
				<view class="cu-item goods" :class="modalName=='move-box-'+ 1?'move-cur':''" @touchstart="ListTouchStart" @touchmove="ListTouchMove"
				 @touchend="ListTouchEnd" :data-target="'move-box-' + 1" @tap="tapNews(1)">
					<!-- #ifndef MP-TOUTIAO -->
					<view class="cu-avatar round" style="background-image:url(../../static/images/avatar/1.jpg);">
						<view class="cu-tag badge"/>
					</view>
					<!-- #endif -->

					<!-- #ifdef MP-TOUTIAO -->
					<view class="cu-avatar round" style="background-image:url(static/images/avatar/1.jpg);">
						<view class="cu-tag badge"/>
					</view>
					<!-- #endif -->
					<view class="content">
						<view class="text-black">
							<text class="margin-right-xs">仔仔</text>
							<text class="cu-tag bg-blue sm radius">
								<text class="cuIcon-male"></text>
							</text>
						</view>
						<view class="text-gray text-sm text-cut">欢迎使用本模板</view>
						<view class="text-gray text-sm">4小时前</view>
					</view>
					<view class="action">
						<!-- #ifndef MP-TOUTIAO -->
						<view class="cu-avatar radius" style="background-image:url(../../static/images/home/goods/11.png);"/>
						<!-- #endif -->
						
						<!-- #ifdef MP-TOUTIAO -->
						<view class="cu-avatar radius" style="background-image:url(static/images/home/goods/11.png);"/>
						<!-- #endif -->
					</view>
					<view class="move">
						<view class="bg-grey">置顶</view>
						<view class="bg-red">删除</view>
					</view>
				</view>
				
				<view class="cu-item goods" :class="modalName=='move-box-'+ 2?'move-cur':''" @touchstart="ListTouchStart" @touchmove="ListTouchMove"
				 @touchend="ListTouchEnd" :data-target="'move-box-' + 2" @tap="tapNews(2)">
					<!-- #ifndef MP-TOUTIAO -->
					<view class="cu-avatar round" style="background-image:url(../../static/images/avatar/2.jpg);">
						<view class="cu-tag badge"/>
					</view>
					<!-- #endif -->
					
					<!-- #ifdef MP-TOUTIAO -->
					<view class="cu-avatar round" style="background-image:url(static/images/avatar/2.jpg);">
						<view class="cu-tag badge"/>
					</view>
					<!-- #endif -->
					<view class="content">
						<view class="text-black">
							<text class="margin-right-xs">仔仔22</text>
							<text class="cu-tag bg-pink sm radius">
								<text class="cuIcon-female"></text>
							</text>
						</view>
						<view class="text-gray text-sm text-cut">希望打个赏哦~</view>
						<view class="text-gray text-sm">6小时前</view>
					</view>
					<view class="action">
						<!-- #ifndef MP-TOUTIAO -->
						<view class="cu-avatar radius" style="background-image:url(../../static/images/home/goods/10.png);"/>
						<!-- #endif -->
						
						<!-- #ifdef MP-TOUTIAO -->
						<view class="cu-avatar radius" style="background-image:url(static/images/home/goods/10.png);"/>
						<!-- #endif -->
					</view>
					<view class="move">
						<view class="bg-grey">置顶</view>
						<view class="bg-red">删除</view>
					</view>
				</view>
				
			</view>
		</view>
		
		<!--占位底部距离-->
		<view class="cu-tabbar-height"></view>
	</view>
</template>

<script>
	import barTitle from '@/zaiui/components/basics/bar-title';
	
	import _tool from '@/util/tools.js';	//工具函数
	export default {
		name: 'news',
		components: { 
			barTitle
		},
		data() {
			return {
				modalName: null, listTouchStart: 0, listTouchDirection: null,
			}
		},
		props: {
			show: {
				type: Boolean,
				default: true
			},
			scrollY: {
				type: Number,
				default: 0
			},
			scrollBottom: {
				type: Number,
				default: 0
			}
		},
		watch: {
			scrollY() {
				//通知他妈的滚动了。
				this.setPageScroll(this.scrollY);
			},
			scrollBottom() {
				if(this.scrollBottom != 0) {
					//通知他妈的触底了
					this.setReachBottom();
				}
			},
		},
		created() {
			//加载虚拟数据
		},
		mounted() {
			_tool.setBarColor(true);
			uni.pageScrollTo({
			    scrollTop: 0,
			    duration: 0
			});
		},
		methods: {
			//页面被滚动
			setPageScroll(scrollTop) {
				//console.log(scrollTop);
			},
			//触底了
			setReachBottom() {
				console.log('触底了');
			},
			barTitleRightTap() {
				console.log('标题栏右边被点击');
			},
			// ListTouch触摸开始
			ListTouchStart(e) {
				this.listTouchStart = e.touches[0].pageX
			},
			// ListTouch计算方向
			ListTouchMove(e) {
				this.listTouchDirection = e.touches[0].pageX - this.listTouchStart > 0 ? 'right' : 'left'
			},
			// ListTouch计算滚动
			ListTouchEnd(e) {
				if (this.listTouchDirection == 'left') {
					this.modalName = e.currentTarget.dataset.target
				} else {
					this.modalName = null
				}
				this.listTouchDirection = null
			},
			//被点击
			tapNews(index) {
				console.log(index);
				if(index == 0) {
					uni.navigateTo({
						url: '/pages/news/notice',
					});
				} else if (index == 1) {
					uni.navigateTo({
						url: '/pages/news/chat',
					});
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
	@import "../../../zaiui/style/news.scss";
	
</style>
