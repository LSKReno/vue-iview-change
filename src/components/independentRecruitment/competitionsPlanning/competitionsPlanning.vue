<template>
    <div>
        <i-input
            v-model="searchedUniversity"
            icon="ios-search-strong"
            placeholder="搜索高校"
            style="width: 200px"
        ></i-input>
        <i-button
            class="font"
            type="ghost"
            shape="circle"
            icon="ios-search"
            @click="searchUniversity"
        ></i-button>

        <Modal class="modal" v-model="universityModal" width="800">
            <p
                slot="header"
                style="color:rgb(241, 123, 123);   text-align:center;font-size:1.25rem;"
            >东北大学</p>

            <div class="school clearfix">
                <div class="schoolLogo clearfix">
                    <img src="https://static-data.eol.cn/upload/logo/134.jpg" alt="..">
                </div>
                <div class="schoolName clearfix">
                    <div class="line1">
                        <span class="line1-schoolName">东北大学</span>
                    </div>
                    <div class="line2">
                        <span class="line2-intro">
                            <a href="http://www.eol.cn/html/g/gxmd/985.shtml" target="_blank">985院校</a>
                        </span>
                        <span class="line2-intro">
                            <a href="http://www.eol.cn/html/g/gxmd/211.shtml" target="_blank">211院校</a>
                        </span>
                        <span class="line2-intro"><i>一流大学建设高校</i></span>
                        <span class="line2-intro"><i>教育部直属</i></span>
                    </div>
                    <div class="line3">
                        <span class="shuxian">院系设置</span>
                        <span class="shuxian">重点学科</span>
                        <span class="shuxian">重点实验室</span>
                        <span class="shuxian">自主招生</span>
                    </div>
                    <div class="line4" style="position: relative;">
                            <span class="line-name">高校类型:</span>
                            <span class="line-value td1">理工类</span>
                            <span class="line-name">所属地区:</span>
                            <span class="line-value td2">辽宁沈阳市</span>
                            <span class="line-name">电子邮箱:</span>
                            <span class="line-value">ddzsb@mail.neu.edu.cn</span>
                            <span class="emailshow">ddzsb@mail.neu.edu.cn</span>
                    </div>
                    <div class="line5" style="position: relative;">
                        <span class="line-name">学历层次:</span>
                        <span class="line-value td1">普通本科</span>
                        <span class="line-name">招办电话:</span>
                        <span class="line-value school-phone td2">024-83687392,024-23891272</span>
                        <span class="line-name">招办网址:</span>
                        <a target="_blank" class="line-value school-net" href="http://zs.neu.edu.cn/">http://zs.neu.edu.cn/</a>
                        <span class="phoneshow">024-83687392,024-23891272</span>
                    </div>
                </div>
            </div>



            <div slot="footer">
                <i-button
                    type="circle"
                    size="large"
                    style="width:100%;background-color:#ff9999;color:white;"
                    @click="universityModal=false"
                >我知道啦</i-button>
            </div>
        </Modal>
        <div class="font">
            <br>省份、学校：
            <Cascader
                :data="data1"
                trigger="hover"
                placeholder="请选择省份、学校"
                class="cascader"
                change-on-select
            ></Cascader>
        </div>
        <div class="font">
            <br>专业：
            <Cascader
                :data="data2"
                trigger="hover"
                placeholder="请选择专业"
                class="cascader"
                change-on-select
            ></Cascader>
        </div>
        <div>
            <br>
            <br>
            <i-button class="font" type="ghost" shape="circle">优惠政策</i-button>
        </div>
        <div>
            <br>
            <br>
            <i-button
                class="competitionsPlanning-queding-button font"
                type="ghost"
                shape="circle"
            >确定</i-button>
            <i-button class="competitionsPlanning-reset-button font" type="ghost" shape="circle">重置</i-button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            universityModal:false,
            searchedUniversity: "",
            competitionsPlanningModal: false,
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
            ],
            data2: [
                {
                    value: "gongke",
                    label: "工科",
                    children: [
                        {
                            value: "ruanjiangongcheng",
                            label: "软件工程"
                        },
                        {
                            value: "jisuanji",
                            label: "计算机技术"
                        },
                        {
                            value: "walawala",
                            label: "哇啦哇啦专业"
                        }
                    ]
                }
            ]
        };
    },
    methods: {
        searchUniversity() {
            if (this.searchedUniversity == "") {
                this.$Message.info("亲爱的, 请输入院校名称关键字");
            } else {
                if (this.searchedUniversity == "东北大学") {
                    this.universityModal = true;
                } else {
                    this.$Message.info(
                        "对不起，您搜索的 " +
                            this.searchedUniversity +
                            " 院校不存在"
                    );
                }
            }
        }



    }
};
</script>

<style scoped>

.school {
    width: 100%;
    margin-top: 60px;
}
.clearfix {
    zoom: 1;
}
.schoolLogo {
    float: left;
    width: 250px;
    padding: 20px;
}
.schoolName .line1 .line1-schoolName {
    font-size: 26px;
    color: #0592dc;
}
.schoolName .line1 span, .schoolName .line2 span {
    cursor: pointer;
}
.schoolName span {
    margin-right: 10px;
}
.schoolName .line2 .line2-intro {
    display: inline-block;
    padding: 0px 1px;
    color: #333;
    border: 1px solid #d0d0d0;
}
.schoolName .line1 span, .schoolName .line2 span {
    cursor: pointer;
}
.schoolName span {
    margin-right: 10px;
}
.schoolName .line3 {
    margin-bottom: 20px;
}




.cascader {
    width: 20%;
}
.font {
    color: aliceblue;
}
.competitionsPlanning-queding-button {
    position: fixed;
    margin-bottom: 1.875rem;
    margin-left: 28.125rem;
    width: 6.25rem;
    /* margin-bottom: 30px;
    margin-left:450px;
    width: 100px */
}
.competitionsPlanning-reset-button {
    position: fixed;
    margin-bottom: 1.875rem;
    margin-left: 37.5rem;
    width: 6.25rem;
    /* margin-bottom: 30px;
    margin-left: 600px;
    width: 100px */
}
</style>
