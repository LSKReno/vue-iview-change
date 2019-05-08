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
                    <img style="width:100%;height:auto;" src="https://wx2.sinaimg.cn/mw1024/006hpJxDly1g2fw9yo4poj31900u0u10.jpg" >
                  </div>
              </CarouselItem>
              <CarouselItem>
                 <div style="display:flex;align-items:center;justify-content:center;">
                    <img style="width:100%;height:auto;" src="https://wx4.sinaimg.cn/mw1024/006hpJxDly1g2fwanqc5aj31900u0u0x.jpg" >
                  </div>
              </CarouselItem>
              <CarouselItem>
                  <div style="display:flex;align-items:center;justify-content:center;">
                    <img style="width:100%;height:auto;" src="https://wx3.sinaimg.cn/mw1024/006hpJxDly1g2u5vpixqbj31av0u01l0.jpg" >
                  </div>
              </CarouselItem>
              <CarouselItem>
                  <div style="display:flex;align-items:center;justify-content:center;">
                    <img style="width:100%;height:auto;" src="https://wxt.sinaimg.cn/mw1024/006hpJxDly1g2fwa16b1zj31900u0qva.jpg?tags=%5B%5D" >
                  </div>
              </CarouselItem>
          </Carousel>
        </Col>
      
        <Col span="10">
          <Card>
            <p slot="title">{{title1}}</p>
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
            <p slot="title">{{title2}}</p>
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
            <p slot="title">{{title3}}</p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
            <p><a class="link-a" @click="guideText">{{title2}}</a></p>
          </Card>
        </Col>
    </Row>
    <Modal class="modal" v-model="modal" width="1400" @on-ok="ok" @on-cancel="cancel">
      <p>{{title1}}</p>
    </Modal>
	</div>

</template>

<script>
  export default {
    data () {
      return {
        title1: '自主招生白问百答',
        title2: '最新自招政策解读',
        title3: '教育部相关文件解释',
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
<style>
  .link-a{
    font-size: 25px;
    color: rgba(228, 217, 217, 0.945);
  }
</style>