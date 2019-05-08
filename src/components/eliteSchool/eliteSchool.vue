<template>
  <div class="font">
        <div class="breadcrumb">
					<Breadcrumb  separator=">" > 
						<Breadcrumb-item class="font" href="/buttonHome">
							<Icon type="ios-home-outline"></Icon>首页
						</Breadcrumb-item>
						<Breadcrumb-item >
							<Icon type="ios-search"></Icon>名校直通车
						</Breadcrumb-item>
					</Breadcrumb>
			</div>
		<br><br>

		<div>
			<Button class="back-button" type="text" @click="backToButtonHome" >
				<Icon type="android-arrow-back" size="32" color="#fff"></Icon>
			</Button>
		</div>
		
		<div>
			<i-input icon="ios-search-strong" placeholder="搜索高校" style="width: 200px"></i-input> <i-button class="font" type="ghost" shape="circle" icon="ios-search"></i-button>
			<br><br>
		</div>
		
  </div>
</template>

<script>
export default {
	data(){
		return {
			
		}
	},
	methods: {
		backToButtonHome () {
            this.$router.push({
                 path: '/buttonHome'
            });        
        }
	}
}
</script>

<style>
.back-button{
	position: fixed;
	bottom: 2rem;
}
.breadcrumb{
	padding:0.65rem;
	background-color: aliceblue
}
.font{
	color: aliceblue
}
</style>
