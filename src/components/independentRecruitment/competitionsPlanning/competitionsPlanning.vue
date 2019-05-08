<template>
  <div>
    <i-input v-model="searchedUniversity" icon="ios-search-strong" placeholder="搜索高校" style="width: 200px"></i-input> 
    <i-button  class="font" type="ghost" shape="circle" icon="ios-search" @click="searchUniversity"></i-button>
    <div class="font">
      <br>
      省份、学校：
      <Cascader :data="data1" trigger="hover" placeholder="请选择省份、学校" class="cascader"  change-on-select></Cascader>
    </div>
    <div class="font">
      <br>
      专业：
      <Cascader :data="data2" trigger="hover" placeholder="请选择专业" class="cascader" change-on-select></Cascader>
    </div>
    <div>
      <br><br>
      <i-button class="font" type="ghost" shape="circle">优惠政策</i-button>
    </div>
    <div>
      <br><br>
      <i-button class="competitionsPlanning-queding-button font" type="ghost" shape="circle">确定</i-button>
      <i-button class="competitionsPlanning-reset-button font" type="ghost" shape="circle">重置</i-button>
    </div>
  </div> 
</template>

<script>
    export default {
        data () {
            return {
                searchedUniversity: "",
                
                data1: [{
                    value: 'beijing',
                    label: '北京',
                    children: [
                        {
                            value: 'beijingdaxue',
                            label: '北京大学'
                        },
                        {
                            value: 'qinghuadaxue',
                            label: '清华大学'
                        },
                        {
                            value: 'beijinghangkonghangtiandaxue',
                            label: '北京航空航天大学'
                        }
                    ]
                }, 
                {
                    value: 'liaoning',
                    label: '辽宁',
                    children: [
                        {
                            value: 'dongbeidaxue',
                            label: '东北大学'
                        },
                        {
                            value: 'dalianligongdaxue',
                            label: '大连理工大学'
                        }
                    ],
                }]
              ,
              data2:[{
                    value: 'gongke',
                    label: '工科',
                    children: [
                        {
                            value: 'ruanjiangongcheng',
                            label: '软件工程'
                        },
                        {
                            value: 'jisuanji',
                            label: '计算机技术'
                        },
                        {
                            value: 'walawala',
                            label: '哇啦哇啦专业'
                        }
                    ]
              }]
            }
        },
        methods: {
            searchUniversity(){
                    if(this.searchedUniversity==""){
                        this.$Message.info("亲爱的, 请输入院校名称关键字");
                    }else{

                    }
            }
        },
        
    }
</script>

<style scoped>
.cascader{
  width: 20%
}
.font{
    color: aliceblue
}
.competitionsPlanning-queding-button{
    position: fixed;
    margin-bottom: 1.875rem;
    margin-left:28.125rem;
    width: 6.25rem
    /* margin-bottom: 30px;
    margin-left:450px;
    width: 100px */
}
.competitionsPlanning-reset-button{
    position: fixed;
    margin-bottom: 1.875rem;
    margin-left: 37.5rem;
    width: 6.25rem
    /* margin-bottom: 30px;
    margin-left: 600px;
    width: 100px */
}


</style>
