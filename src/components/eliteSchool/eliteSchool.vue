<template>
    <div class="font">
        <!-- <div class="breadcrumb"><Breadcrumb separator=">"><Breadcrumb-item class="font" href="/buttonHome"><Icon type="ios-home-outline"></Icon>首页</Breadcrumb-item><Breadcrumb-item><Icon type="ios-search"></Icon>政策解读</Breadcrumb-item></Breadcrumb></div> -->
        <br>
        <h1 class="h-AJK">&nbsp;&nbsp;&nbsp;爱简课</h1>
        <br>
        <br>

        <div>
            <Button class="back-button" type="text" @click="backToButtonHome">
                <Icon type="android-arrow-back" size="32" color="#fff"></Icon>
            </Button>
        </div>

        <div class="flex-div">
            <div class="selector-div">
                <!-- <al-selector style="width:250px"  level="0" data-type="name" @on-change="change" /> 用on-change也可以实现-->
                <al-selector
                    style="width:210px;"
                    level="0"
                    @on-change="send"
                    data-type="name"
                    v-model="sname"
                    searchable
                    size="large"
                />
            </div>

            <div class="card-div">
                <Card :bordered="false" class="PCard">
                    <Row :gutter="64">
                        <Col span="12">
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
                                    <div
                                        style="display:flex;align-items:center;justify-content:center;"
                                    >
                                        <img
                                            style="width:100%;height:auto;"
                                            src="https://wx2.sinaimg.cn/mw1024/006hpJxDly1g3semsai1qj30b907ejrj.jpg"
                                        >
                                    </div>
                                </CarouselItem>
                                <CarouselItem>
                                    <div
                                        style="display:flex;align-items:center;justify-content:center;"
                                    >
                                        <img
                                            style="width:100%;height:auto;"
                                            src="https://wx1.sinaimg.cn/mw1024/006hpJxDly1g3sekvartaj30fa0aat98.jpg"
                                        >
                                    </div>
                                </CarouselItem>
                                <CarouselItem>
                                    <div
                                        style="display:flex;align-items:center;justify-content:center;"
                                    >
                                        <img
                                            style="width:100%;height:auto;"
                                            src="https://wx4.sinaimg.cn/mw1024/006hpJxDly1g3sekvbw4jj30i109vjrn.jpg"
                                        >
                                    </div>
                                </CarouselItem>
                                <CarouselItem>
                                    <div
                                        style="display:flex;align-items:center;justify-content:center;"
                                    >
                                        <img
                                            style="width:100%;height:auto;"
                                            src="https://wx4.sinaimg.cn/mw1024/006hpJxDly1g3sekvbwgjj30ci08h0sw.jpg"
                                        >
                                    </div>
                                </CarouselItem>
                            </Carousel>
                        </Col>

                        <Col span="12">
                            <Card :bordered="false" class="Card">
                                <p slot="title" style="font-size:1.25rem">名校直通资讯</p>
                                <p>
                                    <a
                                        class="link-a"
                                        @click="guideText"
                                    >l&nbsp;&nbsp;&nbsp;孩子马上高考,高校专项计划这个东西,你真正的了解吗?</a>
                                </p>
                                <hr>
                                <p>
                                    <a
                                        class="link-a"
                                        @click="guideText"
                                    >l&nbsp;&nbsp;&nbsp;2019高考降分录取!除了自主招生,还有综合评价、专项计划</a>
                                </p>
                                <hr>
                                <p>
                                    <a
                                        class="link-a"
                                        @click="guideText"
                                    >l&nbsp;&nbsp;&nbsp;农村专项计划的利弊 有什么好处</a>
                                </p>
                            </Card>
                        </Col>
                    </Row>
                    <br>
                    <br>
                    <Row :gutter="64">
                        <Col span="12">
                            <Card :bordered="false" class="Card">
                                <p slot="title" style="font-size:1.25rem">{{sname[0]}}</p>
                                <p>
                                    <a
                                        class="link-a"
                                        @click="guideText(index)"
                                    >
                                        高校专项计划，是国家为更好地促进教育公平、让更多的农村学生上大学而出台的一项优惠政策。、
																				定向招收边远、贫困、民族等地区县（含县级市）以下高中勤奋好学、成绩优良的农村学生，
																				招生高校为教育部直属高校和其他自主招生试点高校。
                                    </a>
                                </p>
                            </Card>
                        </Col>
                        <Col span="12">
                            <Card :bordered="false" class="Card">
                                <p slot="title" style="font-size:1.25rem">高校专项计划</p>
                                <p>
                                    <a class="link-a" @click="guideText">>南京大学（2019）高校专项招生简章</a>
                                </p>
                                <p>
                                    <a class="link-a" @click="guideText">>东北大学（2019）高校专项招生简章</a>
                                </p>
                                <p>
                                    <a class="link-a" @click="guideText">>北京大学（2019）高校专项招生简章</a>
                                </p>
                                <p>
                                    <a class="link-a" @click="guideText">>南方科技大学（2019）高校专项招生简章</a>
                                </p>
                            </Card>
                        </Col>
                    </Row>
                </Card>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            count: 0,
            modal: false,
            policyList: [],
            sname: ["高校专项计划"],
            title1: "自主招生百问百答",
            title2: "最新自招政策推荐",
            title3: "教育部最新文件以及相应解释",
            content: "",
            value2: 0,
            setting: {
                height: 300,
                autoplay: true,

                autoplaySpeed: 4000,
                dots: "inside",
                radiusDot: false,
                trigger: "click",
                arrow: "always"
            }
        };
    },
    methods: {
        send() {
            this.$http({
                method: "post",
                url:
                    "https://fantuan.wxhulu.com:8086/newEntrancePolicy/getProvince/getNewEntrancePolicy",
                data: {
                    province: this.sname[0]
                }
            })
                .then(resp => {
                    console.log(resp);
                    this.policyList = resp.data.data;
                    // this.title2=resp.data.data[0].title;
                    // this.content=resp.data.data[0].content;
                })
                .catch(resp => {
                    console.log(
                        "请求失败：" + resp.status + "," + resp.statusText
                    );
                });
        },
        backToButtonHome() {
            this.$router.push({
                path: "/buttonHome"
            });
        },
        guideText(data) {
            this.modal = true;
            this.count = data - 1;
        }
        // change(data){
        // 	this.sname = data;
        // },对应上方注释
    }
};
</script>

<style>
.flex-div {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
}
.selector-div {
    float: left;
}
.card-div {
    width: 75rem;
    float: right;
}
.h-AJK {
    font-size: 2.5rem;
}
.PCard {
    background-color: rgb(77, 182, 164, 0.5);
}
.Card {
    background-color: rgb(77, 182, 164, 0.2);
}
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
.link-a {
    font-size: 1.25rem;
    color: rgba(228, 217, 217, 0.945);
}
.right-col-textarea {
    float: right;
    background-color: aliceblue;
}
</style>
