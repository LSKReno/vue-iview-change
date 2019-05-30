<template>
	<div class="font">
		<i-input v-model="searchedUniversity" icon="ios-search-strong" placeholder="搜索高校" style="width: 200px"></i-input> 
        <i-button  class="font" type="ghost" shape="circle" icon="ios-search" @click="searchUniversity"></i-button>
        
        <Modal class="modal" v-model="universityModal" width="800">
            <p slot="header"
                style="color:rgb(241, 123, 123);   text-align:center;font-size:1.25rem;">东北大学</p>
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

		<br><br>
		<i-table :content="self" height="250" class="tabel" size="small" :columns="columns1" :data="tableData"></i-table>
        
        <div class="block">
            <div class="competitions-type oneone">
                自然科学类

                <div class="competitions-type2">
                    （1）数学类
                </div>
                <Cascader id="math" class="cascader" :data="math" placeholder="请选择比赛及所获奖项" trigger="hover" @on-change="changeToTable" change-on-select></Cascader>
                
                <div class="competitions-type2">
                    （2）物理类
                </div>
                <Cascader id="physics" class="cascader" :data="physics" placeholder="请选择比赛及所获奖项" trigger="hover" @on-change="changeToTable" change-on-select></Cascader>
                
                <div class="competitions-type2">
                    （3）生物类
                </div>
                <Cascader id="biology" class="cascader" :data="biology" placeholder="请选择比赛及所获奖项" trigger="hover" @on-change="changeToTable" change-on-select></Cascader>
                
                <div class="competitions-type2">
                    （4）化学类
                </div>
                <Cascader id="chemistry" class="cascader" :data="chemistry" placeholder="请选择比赛及所获奖项" trigger="hover" @on-change="changeToTable" change-on-select></Cascader>
            </div>

            <div class="competitions-type onetwo">
                人文类
                <div class="competitions-type2">
                    （1）语文类
                </div>
                <Cascader  id="language" class="cascader" :data="language" placeholder="请选择比赛及所获奖项" trigger="hover" @on-change="changeToTable" change-on-select></Cascader>
                <div class="competitions-type2">
                    （2）作文类
                </div>
                <Cascader id="composition" class="cascader" :data="composition" placeholder="请选择比赛及所获奖项" trigger="hover" @on-change="changeToTable" change-on-select></Cascader>
            </div>

            <div class="competitions-type twoone">
                外语类
                <div class="competitions-type2">
                    （1）英语类
                </div>
                <Cascader  id="english" class="cascader" :data="english" placeholder="请选择比赛及所获奖项" trigger="hover" @on-change="changeToTable" change-on-select></Cascader>
                <div class="competitions-type2">
                    （2）日语类
                </div>
                <Cascader id="japanese" class="cascader" :data="japanese" placeholder="请选择比赛及所获奖项" trigger="hover" @on-change="changeToTable" change-on-select></Cascader>
            </div>

            <div class="competitions-type twotwo">
                信息学类
                <div class="competitions-type2">
                    （1）计算机科学与软件类
                </div>
                  <Cascader  id="programe" class="cascader" :data="programe" placeholder="请选择比赛及所获奖项" trigger="hover" @on-change="changeToTable" change-on-select></Cascader>
            </div>
        </div>

        <Modal class="modal" v-model="recommendedModal" width="800">
            <p slot="header"
                style="color:rgb(241, 123, 123);   text-align:center;font-size:1.25rem;">院校推荐</p>
            <!-- <p>东北大学</p>
            <p>浙江大学</p>
            <p>南方科技大学</p> -->

            <p>华东师范大学</p>
            <p>北京师范大学</p>
            <p>上海戏剧学院</p>



            <div slot="footer">
                <i-button
                    type="circle"
                    size="large"
                    style="width:100%;background-color:#ff9999;color:white;"
                    @click="recommendedModal=false"
                >我知道啦</i-button>
            </div>
        </Modal>

        
        

		<br><br>
      	<i-button class="universityRecommand-queding-button font" type="ghost" shape="circle" @click="recommendUniversity">确定</i-button>
      	<i-button class="universityRecommand-reset-button font" type="ghost" shape="circle" @click="reset" >重置</i-button>
	</div>
</template>

<script>
    export default {
        data () {
            return {
                universityModal: false,
                recommendedModal:false ,
                self: this,
                searchedUniversity: "",
                columns1: [
                    {
                        title: '比赛名称',
                        key: 'name'
                    },
                    {
                        title: '比赛所获奖项',
                        key: 'award'
                    },
                    {
                        title: '操作',
                        key: 'action',
                        width: 150,
                        align: 'center',
                        render: (h, params) => {
                            return h('div', [
                                h('Button', {
                                props: {
                                    type: 'success',
                                    size: 'small'
                                },
                                style: {
                                    marginRight: '5px'
                                },
                                on: {
                                    click: () => {
                                    this.show(params.index)
                                    }
                                }
                                }, '查看'),
                                h('Button', {
                                props: {
                                    type: 'error',
                                    size: 'small'
                                },
                                on: {
                                    click: () => {
                                    this.remove(params.index)
                                    }
                                }
                                }, '删除')
                            ]);
                        }
                    }
                ],
                tableData: [
                    // {
                    //     name: 'XX作文大赛',
                    //     award: '一等奖',
                    // },
                    // {
                    //     name: 'XX大赛',
                    //     award: '特等奖',
                    // }
				],
				math: [{
                    value: 'XX数学大赛',
                    label: 'XX数学大赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                },{
                    value: 'OO数学大赛',
                    label: 'OO数学大赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                }
                ],
                physics: [{
                    value: 'XX物理大赛',
                    label: 'XX物理大赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                },{
                    value: 'GG物理大赛',
                    label: 'GG物理大赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                }
                ],
                biology: [{
                    value: 'XX生物大赛',
                    label: 'XX生物大赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                },{
                    value: 'OO生物大赛',
                    label: 'OO生物大赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                }
                ],
                chemistry: [{
                    value: 'XX化学大赛',
                    label: 'XX化学大赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                },{
                    value: 'GG化学大赛',
                    label: 'GG化学大赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                }
                ],
                language: [{
                    value: 'XX语文知识大赛',
                    label: 'XX语文知识大赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                }
                ],
                composition: [{
                    value: 'XX作文大赛',
                    label: 'XX作文大赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                },{
                    value: '新概念作文大赛',
                    label: '新概念作文大赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                }
                ],
                english: [{
                    value: 'XX英语竞赛',
                    label: 'XX英语竞赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                }
                ],
                japanese: [{
                    value: 'XX日语竞赛',
                    label: 'XX日语竞赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                }
                ],
                programe: [{
                    value: 'XX大数据竞赛',
                    label: 'XX大数据竞赛',
                    children: [
                        {
                            value: 'specialPlace',
                            label: '特等奖'
                        },
                        {
                            value: 'firstPlace',
                            label: '一等奖'
                        },
                        {
                            value: 'secondPlace',
                            label: '二等奖'
                        },
                        {
                            value: 'thirdPlace',
                            label: '三等奖'
                        }
                    ]
                }
                ]

            }
        },
        methods: {
            searchUniversity(){
                if(this.searchedUniversity==""){
                    this.$Message.info("亲爱的, 请输入院校名称关键字");
                }else{
                    if(this.searchedUniversity=="东北大学"){
                        this.universityModal = true
                    }else{
                        this.$Message.info("对不起，您搜索的 "+this.searchedUniversity+" 院校不存在");
                    }
                }
            },
            recommendUniversity(){
                this.recommendedModal = true
            },

            // table操作中的方法
            show (index) {
                this.$Modal.info({
                    title: '获奖信息',
                    content: `大赛名称：${this.tableData[index].name}<br>获奖级别：${this.tableData[index].award}`
                })
            },
            remove (index) {
                this.tableData.splice(index, 1);
            },
            changeToTable(labels, selectedData){
                const index = labels.length - 1;
                const data = selectedData[index] || false;
                const tableDataArray = data.__label.split("/");
                // console.log(tableDataArray[0]);
                // console.log(tableDataArray[1]);
                this.tableData.push({ name: tableDataArray[0],award: tableDataArray[1]});
            },
            reset(){
                this.tableData = [];
            }
        },
    }
</script>

<style>
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


.cascader{
  width: 14.375rem
  /* width: 230px */
}
.tabel{
	float: right;
	width: 21.875rem;
	/* width: 350px; */
}
.competitions-type{
	font-size: 1.25rem;
	color: rgb(155, 130, 130)
}
.competitions-type2{
	font-size: 0.75rem;
	color: aliceblue
}
.font{
    color: aliceblue
}
.universityRecommand-queding-button{
    position: fixed;
    margin-left: 28.125rem;
    width: 6.25rem
}
.universityRecommand-reset-button{
    position: fixed;
    margin-left: 37.5rem;
    width: 6.25rem
}
.block{
    width:37.5rem;
    height:22.5rem;
    padding:0;
    margin:0;
}
.oneone{
    width: 18.75rem;
    float: left;
}
.onetwo{
    width: 18.75rem;
    float: left;
}
.twoone{
    width: 18.75rem;
    float: left;
}
.twotwo{
    width: 18.75rem;
    float: left;
}
</style>
