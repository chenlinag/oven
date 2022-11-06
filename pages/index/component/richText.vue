<template>
	<view class='richText' :style="'background-color:'+bgColor+';margin:'+ udConfig +'rpx '+ lrConfig +'rpx;'" v-if="description">
		<!-- <view>大法官好地方规划的法规</view> -->
		<!-- #ifndef APP-PLUS -->
		<jyf-parser :domain='domain' :html="description.replace(/<br\/>/ig, '')" ref="article" :tag-style="tagStyle"></jyf-parser>
		<!-- #endif -->
		<!-- #ifdef APP-PLUS -->
		<view class="description" v-html="description"></view>
		<!-- #endif -->
	</view>
</template>


<script>
	import parser from "@/components/jyf-parser/jyf-parser";
	import { HTTP_REQUEST_URL } from '@/config/app';
	export default {
		name: 'richText',
		props: {
			dataConfig: {
				type: Object,
				default: () => {}
			}
		},
		components: {
			"jyf-parser": parser
		},
		data() {
			return {
				tagStyle: {
					img: 'width:100%;'
				},
				bgColor:this.dataConfig.bgColor.color[0].item,
				lrConfig:this.dataConfig.lrConfig.val,
				description:this.dataConfig.richText.val,
				// description:'<p><video src="https://saga.crmebweb.com/uploads/media/20220823/e7abd1aaa7fbb508571e48f7c1d4c5f9.mp4" style="max-width:100%;" controls="" <="" video=""></video></p>',
				udConfig:this.dataConfig.udConfig.val * 2,
				domain: HTTP_REQUEST_URL,
			};
		},
		created() {
			
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	.richText{
		padding: 20rpx;
		background-color: #fff;
		margin: 0 20rpx;
	}
</style>
