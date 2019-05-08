<template>
 <div id="big"> 
	 <div class="breadcrumb">
					<Breadcrumb  separator=">" > 
						<Breadcrumb-item class="font" href="/buttonHome">
							<Icon type="ios-home-outline"></Icon>首页
						</Breadcrumb-item>
						<Breadcrumb-item >
							<Icon type="ios-search"></Icon>职业测试
						</Breadcrumb-item>
					</Breadcrumb>
	</div>
	<br><br>
	 	<div class="card-style" id="startDiv">
			<div class="question">
				<span>Q {{index+1}}： </span><span>{{allQuestions.questions[index]}}</span>
			</div>
			<br><br><br>
			<div class="answer" v-for="(answer,ind) in allQuestions.answers[index]">
				<i-Button class="font"  type="ghost" @click="uploadAnswer(ind,index)">
					{{answer}}
				</i-Button>
			</div>
		</div>

			<div class="card-style" id="endDiv" hidden="hidden">
				<h3>{{finalComment.title}}</h3>
				<p>{{finalComment.comment}}</p>
				<Button @click="again">再测一次</Button>
			</div>
		
			<Button class="back-button" type="text" @click="backToButtonHome" >
				<Icon type="android-arrow-back" size="32" color="#fff"></Icon>
			</Button>
  </div>

</template>

<script>
export default {
	data(){
		return {
			finalComment:{
				title:"",
				comment:""
			},
			allQuestions:{
				questions:["你走路时是……",
				"和人说话时，你……",
				"你何时感觉最好？",
				"坐著休息时，你的……",
				"碰到你感到发笑的事时，你的反应是……",
				"当你去一个派对或社交场合时，你……",
				"当你非常专心工作时，有人打断你，你会……",
				"下列颜色中，你最喜欢哪一颜色？",
				"你经常梦到你在……",
				"临入睡的前几分钟，你在床上的姿势是……"],
				answers:[["大步的快走","小步的快走","不快，仰著头 8面对著世界","不快，低著头","很慢"],
				["手臂交叠的站著","双手紧握著","一只手或两手放在臀部","碰著或推著与你说话的人","玩著你的耳朵、摸著你的下巴、或用手整理头发"],
				["早晨","下午及傍晚","夜里"],
				["两膝盖并拢","两腿交叉","两腿伸直","一腿卷在身下"],
				["一个欣赏的大笑","笑著，但不大声","轻声的咯咯地笑","羞怯的微笑"],
				["很大声地入场以引起注意","安静地入场，找你认识的人","非常安静地入场，尽量保持不被注意"],
				["欢迎他","感到非常恼怒","在上两极端之间"],
				["红或橘色","黑色","黄或浅蓝色","绿色","深蓝或紫色","白色","棕或灰色"],
				["落下","打架或挣扎","找东西或人","飞或漂浮","你平常不做梦","你的梦都是愉快的"],
				["仰躺，伸直","俯躺，伸直","侧躺，微卷","头睡在一手臂上","被盖过头"]],
				scores:[[6,4,7,2,1],[4,2,5,7,6],[2,4,6],[4,6,2,1],[6,4,3,5],[6,4,2],[6,2,4],[6,7,5,4,3,2,1],
				[4,2,3,5,6,1],[7,6,4,2,1]]
			},
			youQuestions:[],
			index:0,
			comments:[["内向的悲观者","人们认为你是一个害羞的、神经质的、优柔寡断的，是须人照顾、永远要别人为你做决定、不想与任何事或任何人有关。他们认为你是一个杞人忧天者，一个永远看到不存在的问题的人。有些人认为你令人乏味，只有那些深知你的人知道你不是这样的人。"],
			["缺乏信心的挑剔者","你的朋友认为你勤勉刻苦、很挑剔。他们认为你是一个谨慎的、十分小心的人，一个缓慢而稳定辛勤工作的人。如果你做任何冲动的事或无准备的事，你会令他们大吃一惊。他们认为你会从各个角度仔细地检查一切之后仍经常决定不做。他们认为对你的这种反应一部分是因为你的小心的天性所引起的。"],
			["以牙还牙的自我保护者","别人认为你是一个明智、谨慎、注重实效的人。也认为你是一个伶俐、有天赋有才干且谦虚的人。你不会很快、很容易和人成为朋友，但是是一个对朋友非常忠诚的人，同时要求朋友对你也有忠诚的回报。那些真正有机会了解你的人会知道要动摇你对朋友的信任是很难的，但相等的，一旦这信任被破坏，会使你很难熬过。"],
			["平衡的中道","别人认为你是一个新鲜的、有活力的、有魅力的、好玩的、讲究实际的、而永远有趣的人；一个经常是群众注意力的焦点，但是你是一个足够平衡的人，不至於因此而昏了头。他们也认为你亲切、和蔼、体贴、能谅解人；一个永远会使人高兴起来并会帮助别人的人"],
			["吸引人的冒险家","别人认为你是一个令人兴奋的、高度活泼的、相当易冲动的个性；你是一个天生的领袖、一个做决定会很快的人，虽然你的决定不总是对的。他们认为你是大胆的和冒险的，会愿意试做任何事至少一次；是一个愿意尝试机会而欣赏冒险的人。因为你散发的刺激，他们喜欢跟你在一起。"],
			["傲慢的孤独者","别人认为对你必须“小心处理”。在别人的眼中，你是自负的、自我中心的、是个极端有支配欲、统治欲的。别人可能钦佩你，希望能多像你一点，但不会永远相信你，会对与你更深入的来往有所踌躇及犹豫.世界本来就是层层嵌套，周而复始；不以任何的意志而改变"]]
		}
	},
	methods: {
		backToButtonHome () {
            this.$router.push({
                 path: '/buttonHome'
            });        
		},
		startTest(){

		},
		again(){
			this.index=0;
			document.getElementById("startDiv").hidden=null;
			document.getElementById("endDiv").hidden="hidden";
			this.youQuestions=[];
		},
		uploadAnswer(index,newIndex){
			if(newIndex==9){
				let score=0;
				this.youQuestions.push(index)
				console.log(this.youQuestions)
				for(let i=0;i<this.youQuestions.length;i+=1){
					score+=this.allQuestions.scores[i][this.youQuestions[i]]
				}
				if(score<21){
					this.finalComment.title=this.comments[0][0];
					this.finalComment.comment=this.comments[0][1];
				}
				else if(score<=30){
					this.finalComment.title=this.comments[1][0];
					this.finalComment.comment=this.comments[1][1];
				}
				else if(score<=40){
					this.finalComment.title=this.comments[2][0];
					this.finalComment.comment=this.comments[2][1];
				}
				else if(score<=50){
					this.finalComment.title=this.comments[3][0];
					this.finalComment.comment=this.comments[3][1];
				}
				else if(score<=60){
					this.finalComment.title=this.comments[4][0];
					this.finalComment.comment=this.comments[4][1];
				}
				else {
					this.finalComment.title=this.comments[5][0];
					this.finalComment.comment=this.comments[5][1];
					}
				console.log(this.finalComment.title)
				console.log(this.finalComment.comment)
				document.getElementById("startDiv").hidden="hidden";
				document.getElementById("endDiv").hidden=null;

			}
			else{
				this.youQuestions.push(index)
				this.index+=1;
			}
		}
	}
}
</script>

<style>
.question{
	font-family: serif;
	font-size: 2rem;
	display: flex;
	align-items: center;
	justify-content: center;
}
.answer{
	display:flex;
	align-items:center;
	justify-content:center;
}
.card-style{
	background-color: #dd7fbeef;
	width: 50rem;
	height: 22.5rem;
	margin: 5rem auto 0;
	box-shadow: 0.0625rem 0.4375rem 1.5625rem #fd8fd9;
}
.breadcrumb{
	padding:0.65rem;
	background-color: aliceblue
}
.back-button{
	position: fixed;
	bottom: 2rem;
}
.font{
	color: aliceblue
}
#big{
	color:white;
}

</style>
