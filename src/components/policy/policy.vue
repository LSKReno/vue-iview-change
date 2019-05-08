<template>
    <div class="font">
        <div class="breadcrumb">
            <Breadcrumb separator=">">
                <Breadcrumb-item class="font" href="/buttonHome">
                    <Icon type="ios-home-outline"></Icon>首页
                </Breadcrumb-item>
                <Breadcrumb-item>
                    <Icon type="ios-search"></Icon>政策解读
                </Breadcrumb-item>
            </Breadcrumb>
        </div>
        <br>
        <br>

		<div>
			<Button class="back-button" type="text" @click="backToButtonHome" >
				<Icon type="android-arrow-back" size="32" color="#fff"></Icon>
			</Button>
		</div>
		
		<div>
		<!-- 使用栅格构建布局 -->
		<!-- 需要通过选择学校来动态改变内容，所以图片和所有连接不可以写死 -->
    <Row type="flex" justify="space-around" class="code-row-bg">
        <Col span="4" >
          <div class="button-tab">
			      <al-selector style="width:250px"  level="0" data-type="name" @on-change="change" />
          </div>
        </Col>
        <Col span="9">
          <!-- 走马灯 -->
          <Carousel v-model="value2" 
              :height="setting.height"
              :autoplay="setting.autoplay"
              :autoplay-speed="setting.autoplaySpeed"
              :dots="setting.dots"
              :radius-dot="setting.radiusDot"
              :trigger="setting.trigger"
              :arrow="setting.arrow">
              <CarouselItem>
                  <div style="display:flex;align-items:center;justify-content:center;">
                    <img style="width:100%;height:auto;" src="../../assets/independentRecruitmentPolicy/1.jpg" >
                  </div>
              </CarouselItem>
              <CarouselItem>
                 <div style="display:flex;align-items:center;justify-content:center;">
                    <img style="width:100%;height:auto;" src="../../assets/independentRecruitmentPolicy/2.jpg" >
                  </div>
              </CarouselItem>
              <CarouselItem>
                  <div style="display:flex;align-items:center;justify-content:center;">
                    <img style="width:100%;height:auto;" src="../../assets/independentRecruitmentPolicy/3.jpg" >
                  </div>
              </CarouselItem>
              <CarouselItem>
                  <div style="display:flex;align-items:center;justify-content:center;">
                    <img style="width:100%;height:auto;" src="../../assets/independentRecruitmentPolicy/4.jpg" >
                  </div>
              </CarouselItem>
          </Carousel>
        </Col>

        <Col span="9">
          <Card>
            <p slot="title"></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
          </Card>
        </Col>
    </Row>
    <br>
    <br>
    <Row type="flex" justify="space-around" class="code-row-bg">
        <Col span="4">
          <Card>
            <p slot="title">{{name}}</p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
          </Card>
        </Col>
        <Col span="9">
          <Card>
            <p slot="title"></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
          </Card>
        </Col>
        <Col span="9">
          <Card>
            <p slot="title"></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
          </Card>
        </Col>
    </Row>
	</div>
	<Modal class="modal" v-model="modal" width="1400" @on-ok="ok" @on-cancel="cancel">
    <p>{{title1}}</p>
  </Modal>
  </div>
</template>

<script>

export default {
	data(){
		return {
      modal: false,
      name: '无',
			title1: '自主招生百问百答',
      title2: '最新自招政策推荐',
      title3: '教育部最新文件以及相应解释',
      value2: 0,
      setting: {
        height: 300,
        autoplay: true,
        autoplaySpeed: 4000,
        dots: 'inside',
        radiusDot: false,
        trigger: 'click',
        arrow: 'always'
      }
		}
	},
	methods: {
		backToButtonHome () {
            this.$router.push({
                 path: '/buttonHome'
            });        
        },
    change(data){
			this.name = data;
    },
    guideText() {
            this.modal = true;
    }
	}
}
</script>

<style>
.breadcrumb {
    padding: 0.65rem;
    background-color: aliceblue;
}
.font {
    color: aliceblue;
}
.back-button {
    position: fixed;
    bottom: 2rem;
}
.cascader {
    width: 100%;
}
.link-a{
    font-size: 25px;
    color: rgba(228, 217, 217, 0.945);
}
.right-col-textarea {
    float: right;
    background-color: aliceblue;
}
</style>
