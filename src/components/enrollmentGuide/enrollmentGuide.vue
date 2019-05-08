<template>
    <div>
        <div class="font">
            <div class="breadcrumb">
                <Breadcrumb separator=">">
                    <Breadcrumb-item class="font" href="/buttonHome">
                        <Icon type="ios-home-outline"></Icon>首页
                    </Breadcrumb-item>
                    <Breadcrumb-item>
                        <Icon type="ios-search"></Icon>招生简章
                    </Breadcrumb-item>
                </Breadcrumb>
            </div>
            <br>
            <br>

            <div>
                <Button class="back-button" type="text" @click="backToButtonHome">
                    <Icon type="android-arrow-back" size="32" color="#fff"></Icon>
                </Button>
            </div>
        </div>

	
	<div>
		<!-- 使用栅格构建布局 -->
		<!-- 需要通过选择学校来动态改变内容，所以图片和所有连接不可以写死 -->
    <Row type="flex" justify="space-around" class="code-row-bg">
      <Col span="5">
        <div class="button-tab">
          <i-input  icon="ios-search-strong" placeholder="搜索高校" style="width: 270px"></i-input> <i-button class="font" type="ghost" shape="circle" icon="ios-search"></i-button>
          <div class="font">
          <br>
          省份、学校：
          <Cascader :data="data1" trigger="hover" placeholder="请选择省份、学校" class="cascader" style="width: 300px"  change-on-select></Cascader>
          </div>
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
      
        <Col span="8">
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
        <Col span="5">
          <br>
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
        <Col span="8">
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
			title1: '自主招生百问百答',
      title2: '最新自招政策推荐',
      title3: '教育部最新文件以及相应解释',
      value2: 0,
      modal: false,
      setting: {
        height: 300,
        autoplay: true,
        autoplaySpeed: 4000,
        dots: 'inside',
        radiusDot: false,
        trigger: 'click',
        arrow: 'always'
      },
			data1: [{
                    value: 'beijing',
                    label: '北京',
                    children: [
                        {
                            value: "beijingdaxue",
                            label: "北京大学"
                        },
                        {
                            value: "qinghuadaxue",
                            label: "清华大学"
                        },
                        {
                            value: "beijinghangkonghangtiandaxue",
                            label: "北京航空航天大学"
                        }
                    ]
                },
                {
                    value: "liaoning",
                    label: "辽宁",
                    children: [
                        {
                            value: "dongbeidaxue",
                            label: "东北大学"
                        },
                        {
                            value: "dalianligongdaxue",
                            label: "大连理工大学"
                        }
                    ]
                }
            ]
        };
    },
    methods: {
        backToButtonHome() {
            this.$router.push({
                 path: '/buttonHome'
            });        
    },
    guideText() {
            this.modal = true;
        }
    }
};
</script>

<style>
.back-button {
    position: fixed;
    bottom: 2rem;
}
.breadcrumb {
    padding: 0.65rem;
    background-color: aliceblue;
}
.font {
    color: aliceblue;
}
.cascader {
    width: 100%;
}
.button-tab {
    float: left;
}
.link-a{
    font-size: 25px;
    color: rgba(228, 217, 217, 0.945);
}
</style>
