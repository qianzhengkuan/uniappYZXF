<template>
	<view class="user-list u-f-ac animated fadeIn fast">
		<f-image :src="item.userpic"
		errorText="失败"
		imageClass="rounded-circle mr-2" 
		imageStyle="width:100rpx;height:100rpx;font-size:15rpx;"
		@click.stop="openSpace"></f-image>
		<view>
			<view>{{item.username}}</view>
			<view style="display: inline-block;">
				<tag-sex-age :age="item.age" :sex="item.sex"></tag-sex-age>
			</view>
		</view>
		<view class="icon iconfont u-f-ajc" v-show="!hidden"
		:class="[item.isguanzhu?'icon-xuanze-yixuan':'icon-zengjia1']"></view>
	</view>
</template>

<script>
	import tagSexAge from "../../components/common/tag-sex-age.vue";
	import fImage from '@/components/common/f-image.vue';
	export default {
		components:{
			tagSexAge,
			fImage
		},
		props:{
			hidden:{
				type:Boolean,
				default:false
			},
			item:Object,
			index:Number
		},
		methods: {
			openSpace(){
				uni.navigateTo({
					url:"../../pages/user-space/user-space?userid="+this.item.id
				})
			}
		},
	}
</script>

<style scoped>
.user-list{
	margin: 0 20upx; 
	padding: 20upx 0;
	border-bottom: 1upx solid #EEEEEE;
}
.user-list>image{
	width: 100upx;
	height: 100upx;
	border-radius: 100%;
	margin-right: 20upx;
	flex-shrink: 0;
}
.user-list>view:first-of-type{
	flex: 1;
}
.user-list>view:first-of-type>view:first-child{
	font-size: 35upx;
}
.user-list>view:last-of-type{
	width: 80upx;
	color:#CCCCCC;
}
.icon-zengjia1{
	color: #F8791B!important;
}
</style>
