<template>
  <div class="font">
        <div class="breadcrumb">
					<Breadcrumb  separator=">" > 
						<Breadcrumb-item class="font" href="/buttonHome">
							<Icon type="ios-home-outline"></Icon>首页
						</Breadcrumb-item>
						<Breadcrumb-item >
							<Icon type="ios-search"></Icon>查看成绩
						</Breadcrumb-item>
					</Breadcrumb>
				</div>
		<br>	
		
		<div class="container">
			<!-- 左 -->
			<div>
				<div>
					<i-input icon="ios-search-strong" placeholder="搜索高校" style="width: 200px"></i-input> <i-button class="font" type="ghost" shape="circle" icon="ios-search"></i-button>
					<br><br>
				</div>
				<p class="title">教务处成绩查询</p>
				<br>
				<i-select :model.sync="gradeSelection" clearable style="width:200px" label-in-value=true>
						<i-option v-for="item in gradeList" :value="item.value">{{ item.label }}</i-option>
				</i-select>
				<i-button style="color: aliceblue" shape="circle" type="ghost" icon="ios-search-strong" @click="checkScores"> 查询</i-button>
				<br>
				<div class="score">
					<p>亲爱的{{name}}：</p>
					您的省份：{{province}}
					<br>
					您的总成绩为：{{chinese+math+english+physics+chemistry+biology+politics+history+geography}}
					<p>语文成绩：{{chinese}}</p> 
					<p>数学成绩：{{math}}</p> 
					<p>英语成绩：{{english}}</p> 
					<p style="font-size:1.3rem;color: rgb(228, 206, 177)">理科成绩：</p> 
					<p>物理成绩：{{physics}}</p> 
					<p>化学成绩：{{chemistry}}</p> 
					<p>生物成绩：{{biology}}</p>
					<p style="font-size:1.3rem;color: rgb(228, 206, 177)">文科成绩：</p> 
					<p>政治成绩：{{politics}}</p> 
					<p>历史成绩：{{history}}</p> 
					<p>地理成绩：{{geography}}</p> 
				</div>
				<div>
					<Button class="back-button" type="text" @click="backToButtonHome" >
						<Icon type="android-arrow-back" size="32" color="#fff"></Icon>
					</Button>
				</div>
			</div>

			<!-- 中 -->
			<div>
				<p class="title">高考选科推荐</p>
			</div>

			<!-- 右 -->
			<div>
				<p class="title">选科推荐</p>
			</div>

		</div>



			

  </div>
</template>

<script>
export default {
	data(){
		return {
			gradeSelection: "",
			name: "",
			scores: 0, 
			chinese: 0, 
			math: 0, 
			english: 0, 
			physics: 0, 
			chemistry: 0, 
			biology: 0, 
			politics: 0, 
			history: 0, 
			geography: 0, 

			province: "",
			gradeList: [{
					value: 'seniorOne',
          label: '高中一年级'
        },
        {
          value: 'seniorTwo',
          label: '高中二年级'
        },
        {
          value: 'seniorThree',
          label: '高中三年级'
				}
			]

									

		}
	},
	methods: {
		checkScores(){
				console.log(this.gradeSelection);
								
				this.name = "霜降",
				this.province = "辽宁省", 
				this.scores = 0, 
				this.chinese = 118, 
				this.math = 135, 
				this.english = 136, 
				this.physics = 76, 
				this.chemistry = 83, 
				this.biology = 75, 
				this.politics = 75, 
				this.history = 63, 
				this.geography = 70
		},
		backToButtonHome () {
            this.$router.push({
                 path: '/buttonHome'
            });        
    }
	}
}

</script>

<style scoped>
.score{
	background-color: rgb(99, 180, 201);
	font-size: 1rem;
	padding: 2rem;
	margin-top: 1rem;
	margin-left: 3rem;
	margin-right: 10rem;
}
.title{
	font-size: 2rem;
	color: bisque
}
.back-button{
	position: fixed;
	bottom: 2rem;
}
.breadcrumb{
	padding:0.65rem;
	background-color: aliceblue
}
.font{
	color: aliceblue
}
.container{
    display: grid;
 		grid-template-columns: repeat(3, 33.33%);
 		grid-template-rows: repeat(3, 33.33%);
		grid-template-areas: 'a b c'
                         'a b c'
                         'a b c';
}

</style>
