<template>
    <div class="font">
        <div class="breadcrumb">
            <Breadcrumb separator=">">
                <Breadcrumb-item class="font" href="/buttonHome">
                    <Icon type="ios-home-outline"></Icon>首页
                </Breadcrumb-item>
                <Breadcrumb-item>
                    <Icon type="ios-search"></Icon>志愿填报查询
                </Breadcrumb-item>
            </Breadcrumb>
        </div>
        <br>
        <div class="tabs-style">
            <Tabs type="card" name="name1">
                <TabPane label="按分数查询" icon="md-school" name="name1">
                    <Row>
                        <Col span="3">
                            <al-selector
                                style="width:9rem"
                                :not-found-text="['无此省']"
                                level="0"
                                v-model="sNotFound"
                                data-type="name"
                                @on-change="change"
                            />
                        </Col>
                        <Col span="1" style="font-size:1.25rem;">科类 ></Col>
                        <Col span="3" style="font-size:1.25rem;">
                            <RadioGroup v-model="artsAndSciences" type="button" size="large">
                                <Radio label="理科"></Radio>
                                <Radio label="文科"></Radio>
                            </RadioGroup>
                        </Col>
                        <Col span="3" style="font-size:1.25rem;">
                            <Input placeholder="请输入分数..."></Input>
                        </Col>
                        <Col span="3" style="font-size:1.25rem;">
                            &nbsp;
                            <Button shape="circle" icon="ios-search" @click="predict">预测</Button>
                        </Col>
                    </Row>
                </TabPane>
                <TabPane label="按位次查询" icon="md-school" name="name2">
                    <Row>
                        <Col span="3">
                            <al-selector
                                style="width:9rem"
                                :not-found-text="['无此省']"
                                level="0"
                                v-model="sNotFound"
                                data-type="name"
                                @on-change="change"
                            />
                        </Col>
                        <Col span="1" style="font-size:1.25rem;">科类 ></Col>
                        <Col span="3" style="font-size:1.25rem;">
                            <RadioGroup v-model="artsAndSciences" type="button" size="large">
                                <Radio label="理科"></Radio>
                                <Radio label="文科"></Radio>
                            </RadioGroup>
                        </Col>
                        <Col span="3" style="font-size:1.25rem;">
                            <Input placeholder="请输入位次..."></Input>
                        </Col>
                        <Col span="3" style="font-size:1.25rem;">
                            &nbsp;
                            <Button shape="circle" icon="ios-search" @click="predict">预测</Button>
                        </Col>
                    </Row>
                </TabPane>
            </Tabs>
        </div>
        
        <div>
            <li class="listSpan">
                <span class="title">录取概率 ></span>
                <i class="iconfont icon-youhua-"></i>
                <div class="more-search">
                    <span v-for="(c1,index) in choice1" @click="handleClick(index)":class="{'spanActive':current===index}">
                        {{c1}}
                    </span>
                </div>
                <div style="clear: both;"></div>
            </li>
            <li class="listSpan">
                <span class="title">所属地区 ></span>
                <i class="iconfont icon-youhua-"></i>
                <div class="more-search">
                    <span class="spanActive">全部</span>
                    <span class>北京</span>
                    <span class>天津</span>
                    <span class>河北</span>
                    <span class>河南</span>
                    <span class>山东</span>
                    <span class>山西</span>
                    <span class>陕西</span>
                    <span class>内蒙古</span>
                    <span class>辽宁</span>
                    <span class>吉林</span>
                    <span class>黑龙江</span>
                    <span class>上海</span>
                    <span class>江苏</span>
                    <span class>安徽</span>
                    <span class>江西</span>
                    <span class>湖北</span>
                    <span class>湖南</span>
                    <span class>重庆</span>
                    <span class>四川</span>
                    <span class>贵州</span>
                    <span class>云南</span>
                    <span class>广东</span>
                    <span class>广西</span>
                    <span class>福建</span>
                    <span class>甘肃</span>
                    <span class>宁夏</span>
                    <span class>新疆</span>
                    <span class>西藏</span>
                    <span class>海南</span>
                    <span class>浙江</span>
                    <span class>青海</span>
                </div>
                <div style="clear: both;"></div>
            </li>
            <li class="listSpan">
                <span class="title">高校层次 ></span>
                <div class="more-search">
                    <span class="spanActive">全部</span>
                    <span class>985工程</span>
                    <span class>211工程</span>
                    <span class>一流大学建设高校</span>
                    <span class>一流学科建设高校</span>
                    <span class>教育部直属</span>
                    <span class>中央部委</span>
                    <span class>自主招生试点</span>
                </div>
            </li>
            <li class="listSpan">
                <span class="title">录取批次 ></span>
                <div class="more-search">
                    <span class="spanActive">全部</span>
                    <span class>本科提前批</span>
                    <span class>本科批</span>
                    <span class>地方专项计划本科批</span>
                    <span class>专科提前批</span>
                    <span class>专科批</span>
                </div>
                <div style="clear: both;"></div>
            </li>
        </div>

        <div>
            <Input v-model="value" placeholder="输入你的分数" style="width: 300px"/>
            <Button type="primary" @click="match">开始匹配</Button>
        </div>
        <div id="matchedDiv" hidden="hidden">
            <span>你可以填报的学校和专业为</span>
            <div v-for="(uni,index) in sccessUniversity">
                <label>{{index}}.</label>
                <label>{{uni.name}},录取分数为{{uni.score}}</label>
            </div>
        </div>

        <div>
            <Button class="back-button" type="text" @click="backToButtonHome">
                <Icon type="android-arrow-back" size="32" color="#fff"></Icon>
            </Button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            current: 0,
            choice1:["全部","冲刺","稳妥","保底"],
            artsAndSciences: "sciences",
            value: "",
            universities: [
                {
                    name: "清华大学",
                    pro: [
                        { name: "软件工程", score: 700 },
                        { name: "自动化", score: 680 },
                        { name: "汉语言文学", score: 670 }
                    ]
                },
                {
                    name: "东北大学",
                    pro: [
                        { name: "软件工程", score: 630 },
                        { name: "自动化", score: 620 },
                        { name: "汉语言文学", score: 610 }
                    ]
                },
                {
                    name: "成都信息工程学院",
                    pro: [
                        { name: "软件工程", score: 500 },
                        { name: "自动化", score: 480 },
                        { name: "汉语言文学", score: 470 }
                    ]
                }
            ],
            sccessUniversity: []
        };
    },
    methods: {
        handleClick(index){
            this.current = index
        },
        predict() {
            this.$Notice.open({
                title: "推荐规则",
                desc:
                    "1、本系统数据均由高校提供，具备参考价值；\n" +
                    "2、考生输入分数，系统将根据在当省招生的高校录取情况，推荐合适的高校\n" +
                    "3、本系统推荐的院校名单，仅供志愿参考。",
                duration: 6
            });
        },
        backToButtonHome() {
            this.$router.push({
                path: "/buttonHome"
            });
        },
        match() {
            let value = this.value;
            let successMatch = [];
            for (let i = 0; i < this.universities.length; i += 1) {
                const name = this.universities[i].name;
                for (let k = 0; k < this.universities[i].pro.length; k += 1) {
                    let proName = this.universities[i].pro[k].name;
                    let score = this.universities[i].pro[k].score;
                    if (value >= score) {
                        successMatch.push({
                            name: name,
                            pro: proName,
                            score: score
                        });
                    }
                }
            }
            this.sccessUniversity = successMatch;
            document.getElementById("matchedDiv").hidden = null;
        }
    }
};
</script>

<style scoped>
.spanActive{
    color: rgb(77, 161, 240);
}
li {
    margin: 0.2rem;
    padding: 0;
    vertical-align: baseline;
    display: inline;
    line-height: 2.5rem;
    /* float:left; */
}
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
.title::before {
    content: "";
    width: 0.3125rem;
    height: 1rem;
    display: inline-block;
    margin-right: 0.625rem;
    border-radius: 0.25rem;
    background-color: #0d9ae6;
    vertical-align: -0.125rem;
}
.title {
    font-size: 0.9rem;
}
.tabs-style > .ivu-tabs.ivu-tabs-card > .ivu-tabs-bar .ivu-tabs-tab {
    border-radius: 0;
    background: #fff;
}
.tabs-style > .ivu-tabs.ivu-tabs-card > .ivu-tabs-bar .ivu-tabs-tab-active {
    border-top: 1px solid #3399ff;
}
.tabs-style
    > .ivu-tabs.ivu-tabs-card
    > .ivu-tabs-bar
    .ivu-tabs-tab-active:before {
    content: "";
    display: block;
    width: 100%;
    height: 1px;
    background: #3399ff;
    position: absolute;
    top: 0;
    left: 0;
}
</style>
