<template>
	<view>
		<!--标题栏-->
		<bar-title bgColor='bg-white' backText=' '>
			<block slot="content">立即支付</block>
		</bar-title>
		<!--商品信息-->
		<view class="bg-white zaiui-goods-details-box">
			<view class="cu-avatar radius" :style="[{backgroundImage:'url('+ getttImgUrl(goods_img) +')'}]"></view>
			<view class="goods-info-view">
				<view class="text-cut text-black">商品名称 99新 苹果 iPhoneX 256G 银色</view>
				<view class="text-sm text-gray">测试内容1</view>
				<view class="text-sm text-gray">测试内容2</view>
				<text class="text-price text-red text-lg">2999.00</text>
			</view>
		</view>
		
		<view class="text-gray padding-sm">支付方式</view>
		
		<!--支付方式-->
		<view class="bg-white zaiui-pay-view">
			<radio-group class="block" @change="RadioChange">
				<view class="zaiui-pay-bar" @tap="payTap('wechat')">
					<!-- #ifndef MP-TOUTIAO -->
					<view class="cu-avatar sm" style="background-image:url(../../static/zaiui-img/wechat.png)"/>
					<!-- #endif -->
					
					<!-- #ifdef MP-TOUTIAO -->
					<view class="cu-avatar sm" style="background-image:url(static/zaiui-img/wechat.png)"/>
					<!-- #endif -->
					<view class="content">
						<view class="text-black">
							<text class="margin-right-sm">微信支付</text>
							<text class="cu-tag bg-red radius sm">推荐</text>
						</view>
						<view class="text-gray text-sm">亿万用户的选择，更快更安全</view>
					</view>
					<view class="action">
						<radio class="red zaiui-radio" :class="radio=='wechat'?'checked':''" :checked="radio=='wechat'?true:false" value="wechat"/>
					</view>
				</view>
				
				<view class="zaiui-pay-bar" @tap="payTap('alipay')">
					<!-- #ifndef MP-TOUTIAO -->
					<view class="cu-avatar sm" style="background-image:url(../../static/zaiui-img/alipay.png)"/>
					<!-- #endif -->
					
					<!-- #ifdef MP-TOUTIAO -->
					<view class="cu-avatar sm" style="background-image:url(static/zaiui-img/alipay.png)"/>
					<!-- #endif -->
					<view class="content">
						<view class="text-black">
							<text class="margin-right-sm">支付宝支付</text>
							<text class="cu-tag line-red radius sm">HOT</text>
						</view>
						<view class="text-gray text-sm">数亿用户都在用，安全可托付</view>
					</view>
					<view class="action">
						<radio class="red zaiui-radio" :class="radio=='alipay'?'checked':''" :checked="radio=='alipay'?true:false" value="alipay"/>
					</view>
				</view>
			</radio-group>
		</view>
		
		<!--提示信息-->
		<view class="text-gray padding-sm text-sm">
			除平台自营外，应由卖方就所销售物品向买家出具发票等相关凭证。平台不代卖家承担任何责任。
		</view>
		
		<!--底部操作-->
		<view class="zaiui-footer-fixed">
			<view class="bg-white padding-sm flex flex-direction">
				<button class="cu-btn radius bg-red">￥1 立即支付</button>
			</view>
		</view>
		
	</view>
</template>

<script>
	import barTitle from '@/zaiui/components/basics/bar-title';
	import _tool from '@/util/tools.js';	//工具函数
	export default {
		components: {
			barTitle,
		},
		data() {
			return {
				goodsList: [], checkAll: true, goods_img: '../../static/images/home/goods/1.png', radio: 'wechat',
			}
		},
		onLoad() {
			
		},
		onReady() {
			_tool.setBarColor(true);
			uni.pageScrollTo({
			    scrollTop: 0,
			    duration: 0
			});
		},
		methods: {
			getttImgUrl(url) {
				return _tool.getttImgUrl(url);
			},
			RadioChange(e) {
				this.radio = e.detail.value;
			},
			payTap(type) {
				this.radio = type;
			}
		}
	}
</script>

<style lang="scss">
	/* #ifdef APP-PLUS */
		@import "../../static/colorui/main.css";
		@import "../../static/colorui/icon.css";
		@import "../../zaiui/style/app.scss";
	/* #endif */
	@import "../../zaiui/style/pay.scss";
</style>
