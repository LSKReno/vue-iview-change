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
                <!-- <al-selector style="width:210px;" level="0" @on-change="send" data-type="name" v-model="sname" searchable size="large"/> -->
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
                                            src="https://i.loli.net/2019/06/07/5cf9c592dd34463360.jpg"
                                        >
                                    </div>
                                </CarouselItem>
                                <CarouselItem>
                                    <div
                                        style="display:flex;align-items:center;justify-content:center;"
                                    >
                                        <img
                                            style="width:100%;height:auto;"
                                            src="https://i.loli.net/2019/06/07/5cf9c7fd128b559705.jpg"
                                        >
                                    </div>
                                </CarouselItem>
                                <CarouselItem>
                                    <div
                                        style="display:flex;align-items:center;justify-content:center;"
                                    >
                                        <img
                                            style="width:100%;height:auto;"
                                            src="https://i.loli.net/2019/06/07/5cf9c8a254f9b45485.jpg"
                                        >
                                    </div>
                                </CarouselItem>
                                <CarouselItem>
                                    <div
                                        style="display:flex;align-items:center;justify-content:center;"
                                    >
                                        <img
                                            style="width:100%;height:auto;"
                                            src="https://static-data.eol.cn/upload/school/1551166022_6280_thumb.jpg"
                                        >
                                    </div>
                                </CarouselItem>
                            </Carousel>
                        </Col>

                        <Col span="12">
                            <Card :bordered="false" class="Card">
                                <p slot="title" style="font-size:1.25rem">高校招生简章资讯</p>
                                
                                <p>
                                    <a
                                        class="link-a"
                                        @click="guideText"
                                    >l&nbsp;&nbsp;&nbsp;东北大学对高考制度改革的解读</a>
                                </p>
                                <hr>
                                <p>
                                    <a
                                        class="link-a"
                                        @click="guideText"
                                    >l&nbsp;&nbsp;&nbsp;东北大学招生简章发布资讯</a>
                                </p>
                                <hr>
                                <p>
                                    <a
                                        class="link-a"
                                        @click="guideText"
                                    >l&nbsp;&nbsp;&nbsp;东北大学招生简章今日发布</a>
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
                                        v-for="index in policyList.length"
                                        class="link-a"
                                        @click="guideText(index)"
                                    >
                                        {{policyList[index-1].title}}
                                        <p></p>
                                        <Modal
                                            class="modal"
                                            v-model="modal"
                                            v-bind:title="policyList[count].title"
                                            width="1400"
                                            @on-ok="ok"
                                            @on-cancel="cancel"
                                        >
                                            <p>{{policyList[count].content}}</p>
                                        </Modal>
                                    </a>
                                </p>
                            </Card>
                        </Col>
                        <Col span="12">
                            <Card :bordered="false" class="Card">
                                <p slot="title" style="font-size:1.25rem">高校招生简章详情</p>
                                <p>
                                    <a class="link-a" @click="guideText">>东北大学2019年本科生自主招生简章</a>
                                </p>
                                <p>
                                    <a class="link-a" @click="guideText">>东北大学2019年外语类保送生招生简章</a>
                                </p>
                                <p>
                                    <a class="link-a" @click="guideText">>东北大学2019年高水平运动队招生简章</a>
                                </p>
                                <p>
                                    <a class="link-a" @click="guideText">>东北大学2019年艺术类招生简章</a>
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
            sname: ["请先选择省份、学校"],
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
