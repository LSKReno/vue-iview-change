<template>
     
  <div>
    <!-- 使用栅格构建布局 -->
    <Row :gutter="64">
        <Col span="10">
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
                    <img style="width:100%;height:auto;" src="../../../assets/independentRecruitmentPolicy/1.jpg" >
                  </div>
              </CarouselItem>
              <CarouselItem>
                 <div style="display:flex;align-items:center;justify-content:center;">
                    <img style="width:100%;height:auto;" src="../../../assets/independentRecruitmentPolicy/2.jpg" >
                  </div>
              </CarouselItem>
              <CarouselItem>
                  <div style="display:flex;align-items:center;justify-content:center;">
                    <img style="width:100%;height:auto;" src="../../../assets/independentRecruitmentPolicy/3.jpg" >
                  </div>
              </CarouselItem>
              <CarouselItem>
                  <div style="display:flex;align-items:center;justify-content:center;">
                    <img style="width:100%;height:auto;" src="../../../assets/independentRecruitmentPolicy/4.jpg" >
                  </div>
              </CarouselItem>
          </Carousel>
        </Col>
      
        <Col span="10">
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
    <Row :gutter="64">
        <Col span="10">
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
        <Col span="10">
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
    <Modal class="modal" v-model="modal" width="1000" @on-ok="ok" @on-cancel="cancel">
      <p>{{title1}}</p>

       <div slot="footer">
                <i-button
                    type="circle"
                    size="large"
                    style="width:100%;background-color:#ff9999;color:white;"
                    @click="modal=false"
                >我知道啦</i-button>
      </div>
    </Modal>
	</div>
  
</template>
<style>
  .link-a{
    font-size: 25px;
    color: rgba(228, 217, 217, 0.945);
  }
</style>

<script>
  export default {
    data () {
      return {
        title1: '复试高分宝典',
        title2: '复试高分宝典',
        title3: '复试高分宝典',
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
        }
      }
    },
    methods:{
      guideText() {
            this.modal = true;
        }
    }
  }
</script>
