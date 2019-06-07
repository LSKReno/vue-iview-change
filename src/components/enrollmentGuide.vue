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
                        <i-input icon="ios-search-strong" placeholder="搜索高校" style="width: 270px"></i-input>
                        <i-button class="font" type="ghost" shape="circle" icon="ios-search"></i-button>
                        <div class="font">
                            <br>省份、学校：
                            <Cascader
                                :data="data1"
                                trigger="hover"
                                placeholder="请选择省份、学校"
                                class="cascader"
                                style="width: 300px"
                                change-on-select
                            ></Cascader>
                        </div>
                    </div>
                </Col>
                <Col span="9">
                    <!-- 走马灯 -->
                    <Carousel
                        v-model="value2"
                        :height="setting.height"
                        :autoplay="setting.autoplay"
                        :autoplay-speed="setting.autoplaySpeed"
                        :dots="setting.dots"
                        :radius-dot="setting.radiusDot"
                        :trigger="setting.trigger"
                        :arrow="setting.arrow"
                    >
                        <CarouselItem>
                            <div style="display:flex;align-items:center;justify-content:center;">
                                <img
                                    style="width:100%;height:auto;"
                                    src="../../assets/independentRecruitmentPolicy/1.jpg"
                                >
                            </div>
                        </CarouselItem>
                        <CarouselItem>
                            <div style="display:flex;align-items:center;justify-content:center;">
                                <img
                                    style="width:100%;height:auto;"
                                    src="../../assets/independentRecruitmentPolicy/2.jpg"
                                >
                            </div>
                        </CarouselItem>
                        <CarouselItem>
                            <div style="display:flex;align-items:center;justify-content:center;">
                                <img
                                    style="width:100%;height:auto;"
                                    src="../../assets/independentRecruitmentPolicy/3.jpg"
                                >
                            </div>
                        </CarouselItem>
                        <CarouselItem>
                            <div style="display:flex;align-items:center;justify-content:center;">
                                <img
                                    style="width:100%;height:auto;"
                                    src="../../assets/independentRecruitmentPolicy/4.jpg"
                                >
                            </div>
                        </CarouselItem>
                    </Carousel>
                </Col>

                <Col span="8">
                    <Card>
                        <p slot="title"></p>
                        <p>
                            <a id="R1" class="link-a" @click="guideText($event)">{{Rtitle1}}</a>
                        </p>
                        <p>
                            <a id="R2" class="link-a" @click="guideText($event)">{{Rtitle2}}</a>
                        </p>
                        <p>
                            <a id="R3" class="link-a" @click="guideText($event)">{{Rtitle3}}</a>
                        </p>
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
                        <p>
                            <a id="L1" class="link-a" @click="guideText">{{Ltitle1}}</a>
                        </p>
                        <p>
                            <a id="L2" class="link-a" @click="guideText">{{Ltitle2}}</a>
                        </p>
                        <p>
                            <a id="L3" class="link-a" @click="guideText">{{Ltitle3}}</a>
                        </p>
                    </Card>
                </Col>
                <Col span="8">
                    <Card>
                        <p slot="title"></p>
                        <p>
                            <a id="R4" class="link-a" @click="guideText">{{Rtitle4}}</a>
                        </p>
                        <p>
                            <a id="R5" class="link-a" @click="guideText">{{Rtitle5}}</a>
                        </p>
                        <p>
                            <a id="R6" class="link-a" @click="guideText">{{Rtitle6}}</a>
                        </p>
                    </Card>
                </Col>
            </Row>
        </div>

        <Modal class="modal" v-model="modal" width="1000" @on-ok="ok" @on-cancel="cancel">
            <p style="font-size:1.5rem;">{{postTitle}}</p>
            <div>
                <p>{{postContent}}</p>
            </div>
        </Modal>
    </div>
</template>

<script>
import axios from "axios";
export default {
    data() {
        return {
            postTitle: "",
            postContent: "",
            Rtitle1: "北京大学2018年招生章程",
            Rtitle2: "清华大学2017年本科招生章程",
            Rtitle3: "北京化工大学招生简章",
            Rtitle4: "北京工业大学招生简章",
            Rtitle5: "北京外国语大学招生简章",
            Rtitle6: "中央音乐学院招生简章",
            Ltitle1: "中央民族大学招生简章",
            Ltitle2: "北京邮电大学招生简章",
            Ltitle3: "北京理工大学招生简章",

            title2: "最新自招政策推荐",
            title3: "教育部最新文件以及相应解释",
            value2: 0,
            modal: false,

            setting: {
                height: 300,
                autoplay: true,
                autoplaySpeed: 4000,
                dots: "inside",
                radiusDot: false,
                trigger: "click",
                arrow: "always"
            },
            data1: [
                {
                    value: "beijing",
                    label: "北京",
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
        created() {
            // this.$store.dispatch('getEnrollmentGuide')
            this.$http({
                method: "post",
                url: context.state.serviceURL + "/getEnrollmentGuide"
            })
                .then(function(res) {
                    console.log(res);
                    console.log("res.data.title: " + res.data.title);
                })
                .catch(function(err) {
                    console.log("getEnrollmentGuide有点小问题");
                });
        },
        backToButtonHome() {
            this.$router.push({
                path: "/buttonHome"
            });
        },
        guideText(event) {
            var postId = event.currentTarget.getAttribute("id");
            // alert(postId);
            // console.log("postID: ",postId)
            switch (postId) {
                case "R1":
                    this.postTitle = this.Rtitle1;
                    this.postContent = "北京大学招生简章";
                    break;
                case "R2":
                    this.postTitle = this.Rtitle2;
                    this.postContent = "清华大学招生简章";
                    break;
                case "R3":
                    this.postTitle = this.Rtitle3;
                    this.postContent = "北京化工大学招生简章";
                    break;
                case "R4":
                    this.postTitle = this.Rtitle4;
                    this.postContent = "北京工业大学招生简章";
                    break;
                case "R5":
                    this.postTitle = this.Rtitle5;
                    this.postContent = "北京外国语大学招生简章";
                    break;
                case "R6":
                    this.postTitle = this.Rtitle6;
                    this.postContent = "中央音乐学院招生简章";
                    break;
                case "L1":
                    this.postTitle = this.Ltitle1;
                    this.postContent = "中央民族大学招生简章";
                    break;
                case "L2":
                    this.postTitle = this.Ltitle2;
                    this.postContent = "北京邮电大学招生简章";
                    break;
                case "L3":
                    this.postTitle = this.Ltitle3;
                    this.postContent = "北京理工大学招生简章";
                    break;
            }
            // alert(this.data1.postContent)
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
.link-a {
    font-size: 25px;
    color: rgba(228, 217, 217, 0.945);
}
</style>
