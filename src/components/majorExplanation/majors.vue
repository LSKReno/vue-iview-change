<template>
    <div class="font">
        <div class="breadcrumb">
            <Breadcrumb separator=">">
                <Breadcrumb-item href="/buttonHome">
                    <Icon type="ios-home-outline"></Icon>首页
                </Breadcrumb-item>
                <Breadcrumb-item href="/buttonHome/majorExplanation">
                    <Icon type="ios-search"></Icon>专业详解
                </Breadcrumb-item>
                <Breadcrumb-item>
                    <Icon type="ios-search"></Icon>
                    {{breadcrumbMajorType}}
                </Breadcrumb-item>
            </Breadcrumb>
        </div>
        <br>

        <!-- <div>
            <i-table border :columns="columns1" :data="data1"></i-table>
            <i-table border :columns="columns2" :data="data2"></i-table>
            <div style="margin: 10px;overflow: hidden">
                <div style="float: right;">
                    <Page :total="100" :current="1" @on-change="changePage"></Page>
                </div>
            </div>
        </div>-->
        <Modal class="modal" v-model="modal" width="1200" @on-ok="ok" @on-cancel="cancel">
            <p slot="header" style="color:black;text-align:center;font-size:1.25rem;">
                <span>哲学</span>
            </p>

            <div>
                <div class="title">基本信息</div>
                <div class="majorBasicInfo">
                    <p>
                        <span>
                            专业代码:
                            <span>010101&nbsp;&nbsp;</span>
                        </span>
                        <span>
                            专业人气:
                            <span>40794&nbsp;&nbsp;</span>
                        </span>
                        <span>
                            授予学位:
                            <span>哲学学士&nbsp;&nbsp;</span>
                        </span>
                        <span>
                            修业年限:
                            <span>四年&nbsp;&nbsp;</span>
                        </span>
                        <span>
                            学科门类:
                            <span>哲学&nbsp;&nbsp;</span>
                        </span>
                        <span>
                            专业类:
                            <span>哲学类&nbsp;&nbsp;</span>
                        </span>
                        <span>
                            选考（学科）建议:
                            <span>不限&nbsp;&nbsp;</span>
                        </span>
                    </p>
                </div>
                <div>
                    <Row>
                        <Col span="7">
                            <Card style="width:20rem">
                                <chart
                                    id="chart1"
                                    :option="drawChart1"
                                    style="width: 14.375rem; height: 15rem"
                                ></chart>
                            </Card>
                        </Col>
                        <Col span="9">
                            <Card style="width:24rem">
                                <chart
                                    id="chart2"
                                    :option="drawChart2"
                                    style="width: 21.875rem; height: 15rem"
                                ></chart>
                            </Card>
                        </Col>
                        <Col span="8">
                            <Card style="width:24rem">
                                <chart
                                    id="chart3"
                                    :option="drawChart3"
                                    style="width: 24rem; height: 15rem"
                                ></chart>
                            </Card>
                            <!-- <chart id="chart" :option="drawChart" style="width: 230px; height: 150px"></chart> -->
                        </Col>
                    </Row>
                </div>

                <div class="title">专业详解</div>
                <div>
                    <p class="problemTitle">是什么</p>
                    <p>
                        哲学研习中西现代哲学、中西哲学史、伦理学、逻辑学、人类学等方面的基本理论和知识，
                        以世界本原为探究对象，研究自然、社会和人类最普遍的问题，探索人的价值观、人生观和世界观的问题。
                        例如：世界的本质是什么，人类应该怎样活着，人类如何看待死亡等。该专业侧重于学术方面，选择需谨慎。
                        <br>关键词：马克思主义 三观 逻辑 伦理
                    </p>
                    <p class="problemTitle">学什么</p>
                    <p>
                        《西方哲学史》、《中国哲学史》、《马克思主义哲学史》、《现代中国哲学》、《西方现代哲学》、
                        《马克思主义哲学原理》、《技术哲学》、《自然哲学》、《现代西方伦理学》、《逻辑学》
                        部分高校按以下专业方向培养：国学。
                    </p>
                    <p class="problemTitle">干什么</p>
                    <p>
                        深造：考研或者保研，继续哲学方面的学习深造，完成硕士、博士学业后，成为大学教授或者哲学学者；
                        转行：向公务员、编辑、记者、教师等方向发展。
                    </p>
                </div>

                <div class="title">就业行业分布</div>
                <div>
                    <Card style="width:50rem">
                        <chart id="chart4" :option="drawChart4" style="width: 45rem; height: 20rem"></chart>
                    </Card>
                </div>

                <div class="title">专业人气院校</div>
                <div class="zhuanye-table">
                    <table>
                        <thead>
                            <tr>
                                <td rowspan="2" class="td-schoolName">学校名称</td>
                                <td rowspan="2" class="td-specialtyName">专业名称</td>
                                <td rowspan="2">重点专业</td>
                                <td colspan="3">高校层次</td>
                                <td rowspan="2" class="td-compare">高校对比</td>
                            </tr>
                            <tr>
                                <td>教育部直属</td>
                                <td>985大学</td>
                                <td>211大学</td>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td class="hoverschoolname">北京大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>否</td>
                                <td>是</td>
                                <td>是</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">中国人民大学</td>
                                <td class="hoverschoolname">哲学（政治学与经济学（PPE实验班）</td>
                                <td>是</td>
                                <td>是</td>
                                <td>是</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">中国人民大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>是</td>
                                <td>是</td>
                                <td>是</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">北京航空航天大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>否</td>
                                <td>否</td>
                                <td>是</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">北京师范大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>否</td>
                                <td>是</td>
                                <td>是</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">首都师范大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>否</td>
                                <td>否</td>
                                <td>否</td>
                                <td>否</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">中央民族大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>否</td>
                                <td>否</td>
                                <td>是</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">中国政法大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>否</td>
                                <td>是</td>
                                <td>否</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">南开大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>是</td>
                                <td>是</td>
                                <td>是</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">河北大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>是</td>
                                <td>否</td>
                                <td>否</td>
                                <td>否</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">山西大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>否</td>
                                <td>否</td>
                                <td>否</td>
                                <td>否</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">内蒙古大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>否</td>
                                <td>否</td>
                                <td>否</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">辽宁大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>是</td>
                                <td>否</td>
                                <td>否</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">吉林大学</td>
                                <td class="hoverschoolname">哲学（PhilosophyProgram）</td>
                                <td>否</td>
                                <td>是</td>
                                <td>是</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">吉林大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>否</td>
                                <td>是</td>
                                <td>是</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">黑龙江大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>是</td>
                                <td>否</td>
                                <td>否</td>
                                <td>否</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">哈尔滨理工大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>否</td>
                                <td>否</td>
                                <td>否</td>
                                <td>否</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">齐齐哈尔大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>否</td>
                                <td>否</td>
                                <td>否</td>
                                <td>否</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">同济大学</td>
                                <td class="hoverschoolname">哲学</td>
                                <td>否</td>
                                <td>是</td>
                                <td>是</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                            <tr>
                                <td class="hoverschoolname">华东师范大学</td>
                                <td class="hoverschoolname">哲学（非师范）</td>
                                <td>否</td>
                                <td>是</td>
                                <td>是</td>
                                <td>是</td>
                                <td>
                                    <button type="button" class="ant-btn clickbnt">
                                        <i class="iconfont icon-plus"></i>
                                        <span>加入对比</span>
                                    </button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                
            </div>
            <div slot="footer">
                <i-button
                    type="circle"
                    size="large"
                    style="width:100%;background-color:#0592dc;color:white;"
                    @click="modal=false"
                >我知道啦</i-button>
            </div>
        </Modal>

        <table>
            <thead>
                <tr>
                    <td class="all-speciayLeibie">专业类别</td>
                    <td class="all-specialtyName">专业名称</td>
                    <td>报考热度排名</td>
                    <td>层次</td>
                </tr>
            </thead>
            <tbody>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td rowspan="4">哲学类</td>
                    <td class="hoverschoolname">哲学</td>
                    <td>全国25 哲学类1</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">逻辑学</td>
                    <td>全国93 哲学类2</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">宗教学</td>
                    <td>全国714 哲学类4</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">伦理学</td>
                    <td>全国682 哲学类3</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td rowspan="6">经济学类</td>
                    <td class="hoverschoolname">经济学</td>
                    <td>全国1067 经济学类13</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">经济统计学</td>
                    <td>全国1158 经济学类15</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">国民经济管理</td>
                    <td>全国42 经济学类4</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">资源与环境经济学</td>
                    <td>全国199 经济学类7</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">商务经济学</td>
                    <td>全国2 经济学类1</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">能源经济</td>
                    <td>全国200 经济学类8</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td rowspan="2">财政学类</td>
                    <td class="hoverschoolname">财政学</td>
                    <td>全国18 财政学类2</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">税收学</td>
                    <td>全国1179 财政学类16</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td rowspan="8">金融学类</td>
                    <td class="hoverschoolname">金融学</td>
                    <td>全国1033 金融学类12</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">金融工程</td>
                    <td>全国24 金融学类3</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">保险学</td>
                    <td>全国1188 金融学类17</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">投资学</td>
                    <td>全国663 金融学类9</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">金融数学</td>
                    <td>全国123 金融学类6</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">信用管理</td>
                    <td>全国686 金融学类11</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">经济与金融</td>
                    <td>全国115 金融学类5</td>
                    <td>本科</td>
                </tr>
                <tr
                    @click="majorInformation"
                    onmouseover="this.style.backgroundColor='#cae6ab';"
                    onmouseout="this.style.backgroundColor='#d4e3e5';"
                >
                    <td class="hoverschoolname">精算学</td>
                    <td>全国1257 金融学类18</td>
                    <td>本科</td>
                </tr>
            </tbody>
        </table>

        <!-- <div class="card-style"> -->

        <!-- </div> -->

        <Button class="back-button" type="text" @click="backToButtonHome">
            <Icon type="android-arrow-back" size="32" color="#fff"></Icon>
        </Button>
        <Page :total="100" size=small class="pager" page-size=10  />

    </div>
</template>

<script>
import echarts from "echarts";
require("echarts/theme/macarons");
export default {
    data() {
        return {
            modal: false,
            breadcrumbMajorType: "哲学",
            model11: "",
            myChart1: null,
            myChart2: null,
            myChart3: null,
            myChart4: null,
            columns1: [
                {
                    title: "专业类别",
                    key: "majorType"
                }
            ],
            columns2: [
                {
                    title: "专业名称",
                    key: "majorName"
                },
                {
                    title: "层次",
                    key: "level"
                },
                {
                    title: "就业前景",
                    key: "careerProspect"
                },
                {
                    title: "开设院校",
                    key: "openUniversities"
                }
            ],
            data1: [
                {
                    majorType: "哲学"
                }
            ],
            data2: [
                {
                    majorType: "哲学",
                    majorName: ["哲学", "逻辑学", "宗教学", "伦理学"],
                    level: "本科",
                    careerProspect: "就业前景",
                    openUniversities: "开设院校"
                }
            ]
        };
    },
    methods: {
        toCareerProspect() {
            this.$router.push({
                path: "/buttonHome/majorExplanation/majors/careerProspect"
            });
        },
        toOpenUniversities() {
            this.$router.push({
                path: "/buttonHome/majorExplanation/majors/openUniversities"
            });
        },
        backToButtonHome() {
            this.$router.push({
                path: "/buttonHome/majorExplanation"
            });
        },
        majorInformation() {
            this.modal = true;
            this.drawChart1();
            this.drawChart2();
            this.drawChart3();
            this.drawChart4();
        },
        drawChart1() {
            this.myChart1 = this.$echarts.init(
                document.getElementById("chart1"),
                "macarons"
            );

            let option = {
                title: {
                    text: "性别比列",
                    x: "center"
                },
                tooltip: {
                    trigger: "item",
                    formatter: "{a} <br/>{b} : {c} ({d}%)"
                },
                legend: {
                    x: "center",
                    y: "bottom",
                    data: ["女生", "男生"]
                },
                toolbox: {
                    show: true,
                    feature: {
                        mark: { show: true },
                        // dataView : {show: true, readOnly: false},
                        magicType: {
                            show: true,
                            type: ["pie", "funnel"]
                        },
                        restore: { show: true }
                        // saveAsImage : {show: true}
                    }
                },
                calculable: true,
                series: [
                    {
                        name: "性别：",
                        type: "pie",
                        radius: [20, 50],
                        center: ["50%", "50%"],
                        roseType: "radius",
                        label: {
                            normal: {
                                show: false
                            },
                            emphasis: {
                                show: true
                            }
                        },
                        lableLine: {
                            normal: {
                                show: false
                            },
                            emphasis: {
                                show: true
                            }
                        },
                        data: [
                            { value: 60, name: "女生" },
                            { value: 40, name: "男生" }
                        ]
                    }
                ]
            };

            this.myChart1.setOption(option);
            window.onresize = function() {
                this.myChart1.resize();
            };
        },
        drawChart2() {
            this.myChart2 = this.$echarts.init(
                document.getElementById("chart2"),
                "macarons"
            );
            let option = {
                title: {
                    text: "就业率"
                },
                xAxis: {
                    name: "年份（公元）",
                    type: "category",
                    data: ["2016", "2017", "2018"]
                },
                yAxis: {
                    name: "百分比（%）",
                    type: "value"
                },
                tooltip: {
                    trigger: "item",
                    formatter: "{b} : {c} %"
                },
                toolbox: {
                    show: true,
                    feature: {
                        mark: { show: true },
                        restore: { show: true }
                    }
                },
                series: [
                    {
                        data: [70, 85, 85],
                        type: "line"
                    }
                ]
            };
            this.myChart2.setOption(option);
            window.onresize = function() {
                this.myChart2.resize();
            };
        },
        drawChart3() {
            this.myChart3 = this.$echarts.init(
                document.getElementById("chart3"),
                "macarons"
            );
            let option = {
                title: {
                    text: "专业能力图"
                },
                tooltip: {},
                radar: {
                    // shape: 'circle',
                    name: {
                        textStyle: {
                            color: "#fff",
                            backgroundColor: "#999",
                            borderRadius: 3,
                            padding: [3, 5]
                        }
                    },
                    indicator: [
                        { name: "逻辑", max: 6500 },
                        { name: "记忆", max: 16000 },
                        { name: "技术", max: 30000 },
                        { name: "执行", max: 38000 },
                        { name: "思辨", max: 52000 },
                        { name: "创新", max: 25000 }
                    ]
                },
                series: [
                    {
                        name: "专业能力（Professional Ability）",
                        type: "radar",
                        data: [
                            {
                                value: [
                                    4300,
                                    10000,
                                    28000,
                                    35000,
                                    50000,
                                    19000
                                ],
                                name: "专业能力（Professional Ability）"
                            }
                        ]
                    }
                ]
            };
            this.myChart3.setOption(option);
            window.onresize = function() {
                this.myChart3.resize();
            };
        },
        drawChart4() {
            this.myChart4 = this.$echarts.init(
                document.getElementById("chart4"),
                "macarons"
            );
            let option = {
                title: {
                    text: "就业行业分布"
                },
                tooltip: {
                    trigger: "item",
                    formatter: "{b} : {c} %"
                },
                legend: {
                    data: ["行业"]
                },
                grid: {
                    left: "3%",
                    right: "4%",
                    bottom: "3%",
                    containLabel: true
                },
                xAxis: {
                    name: "%",
                    type: "value",
                    boundaryGap: [0, 0.01],
                    axisLabel: {
                        formatter: "{value}%"
                    }
                },
                yAxis: {
                    name: "行业",
                    type: "category",
                    data: [
                        "其他行业",
                        "教育培训",
                        "媒体",
                        "房地产",
                        "金融投资",
                        "服装",
                        "快消",
                        "互联网",
                        "广告",
                        "咨询服务"
                    ]
                },
                series: [
                    {
                        name: "行业",
                        type: "bar",
                        data: [
                            42.51,
                            11.52,
                            10.64,
                            9.7,
                            5.64,
                            4.47,
                            4.4,
                            4.21,
                            3.46,
                            3.45
                        ],
                        itemStyle: {
                            normal: {
                                label: {
                                    show: true, //开启显示
                                    position: "right", //在上方显示
                                    textStyle: {
                                        //数值样式
                                        color: "cornflowerblue",
                                        fontSize: 16
                                    }
                                }
                            }
                        }
                    }
                ]
            };
            this.myChart4.setOption(option);
            window.onresize = function() {
                this.myChart4.resize();
            };
        }
    }
};
</script>

<style scoped>
pager{
    text-align:center;
    margin-left: auto; 
    margin-right: auto;
}
table {
    color: black;
    border: 1px solid black;
    width: 100%;
    border-collapse: collapse;
}
th {
    border: 1px solid black;
    height: 50px;
}
td {
    border: 1px solid black;
    padding: 5px;
}
table tr:nth-child(odd) {
    background: rgb(231, 205, 205);
}
table tr:nth-child(even) {
    background: #caeeee;
}
.title::before {
    content: "";
    width: 5px;
    height: 16px;
    display: inline-block;
    margin-right: 10px;
    border-radius: 4px;
    background-color: #0d9ae6;
    vertical-align: -2px;
}
.title {
    font-size: 1rem;
}
.majorBasicInfo {
    color: rgb(172, 172, 172);
}
.problemTitle {
    color: #058ddc;
}
.major-type-container {
    padding: 0rem;
    margin-left: 6rem;
    margin-right: 10rem;
}
.philosophy {
    font-size: 150%;
    border-radius: 0.9375rem;
    width: 10rem;
    height: 4rem;
    background-color: cornflowerblue;
    color: #f0f8ff;
}
.economic {
    font-size: 150%;
    border-radius: 0.9375rem;
    width: 10rem;
    height: 4rem;
    background-color: cornflowerblue;
    color: #f0f8ff;
}
.engineering {
    font-size: 150%;
    border-radius: 0.9375rem;
    width: 10rem;
    height: 4rem;
    background-color: cornflowerblue;
    color: #f0f8ff;
}
.literature {
    font-size: 150%;
    border-radius: 0.9375rem;
    width: 10rem;
    height: 4rem;
    background-color: cornflowerblue;
    color: #f0f8ff;
}
.pedagogy {
    font-size: 150%;
    border-radius: 0.9375rem;
    width: 10rem;
    height: 4rem;
    background-color: cornflowerblue;
    color: #f0f8ff;
}
.history {
    font-size: 150%;
    border-radius: 0.9375rem;
    width: 10rem;
    height: 4rem;
    background-color: cornflowerblue;
    color: #f0f8ff;
}
.law {
    font-size: 150%;
    border-radius: 0.9375rem;
    width: 10rem;
    height: 4rem;
    background-color: cornflowerblue;
    color: #f0f8ff;
}
.back-button {
    position: fixed;
    bottom: 2rem;
}
.breadcrumb {
    padding: 0.65rem;
    background-color: aliceblue;
}
.i-select {
    width: 14.375rem;
    /* width: 230px */
}
.majors-type {
    font-size: 1.25rem;
    color: rgb(12, 8, 8);
    margin-left: 1rem;
}
.font {
    color: aliceblue;
}
.card-style {
    background-color: #dd7fbeef;
    width: 50rem;
    height: 22.5rem;
    margin: 5rem auto 0;
    box-shadow: 0.0625rem 0.4375rem 1.5625rem #fd8fd9;
}
</style>
