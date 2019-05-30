<style lang="less">
@import "./login.less";
</style>
<template>
    <div>
        <Row>
            <Col span="20">
                <h1>{{ msg }}</h1>
            </Col>
            <Col span="1">
                <i-button
                    type="ghost"
                    icon="monitor"
                    class="screenfull-button"
                    @click="screenFull"
                >全屏</i-button>
            </Col>
            <Col span="3">
                <!-- 登录button -->
                <i-button type="ghost" class="login-button" @click="loginModal">登录</i-button>
            </Col>
        </Row>
        <!-- <br> -->
        <!-- 登录Modal -->
        <Modal class="modal loginModal_bg" v-model="login_modal" width="400">
            <p
                slot="header"
                style="color:rgb(241, 123, 123);   text-align:center;font-size:1.25rem;"
            >
                <span class>欢迎登录</span>
            </p>
            <div>
                <div class="form-con">
                    <Form ref="loginForm" :model="form" :rules="rules">
                        <FormItem prop="userName">
                            <Input v-model="form.userName" placeholder="请输入用户名">
                                <span slot="prepend">
                                    <Icon :size="16" type="person"></Icon>
                                </span>
                            </Input>
                        </FormItem>
                        <br>
                        <FormItem prop="password">
                            <Input type="password" v-model="form.password" placeholder="请输入密码">
                                <span slot="prepend">
                                    <Icon :size="14" type="locked"></Icon>
                                </span>
                            </Input>
                        </FormItem>
                        <br>
                        <!-- <FormItem>
                            <Button class="login-bt" @click="handleSubmit" type="ghost" long>登录</Button>
                        </FormItem>-->
                    </Form>

                    <p class="login-tip">输入任意用户名和密码即可</p>
                </div>
            </div>

            <div slot="footer">
                <i-button
                    type="circle"
                    size="large"
                    style="width:100%;background-color:rgb(241, 123, 123);color:white;"
                    @click="handleSubmit"
                >登录</i-button>
            </div>
        </Modal>

        <div class="allButtons" style="text-align:center;margin:0 auto;">
            <Row>
                <Col span="9">
                    <!-- 自主招生是page1 -->
                    <i-button
                        id="bt1"
                        @click="toIndependentRecruitment"
                        icon="paper-airplane"
                        type="primary"
                        class="students"
                    >自主招生</i-button>
                </Col>
                <Col span="11">
                    <!-- 志愿填报是page4 -->
                    <i-button
                        @click="toVoluntaryReporting"
                        type="primary"
                        icon="clipboard"
                        class="voluntary"
                    >
                        志愿填报
                        <br>查询
                    </i-button>
                </Col>
                <Col span="4">
                    <!-- 查看成绩是page7 -->
                    <i-button
                        @click="toCheckScores"
                        type="primary"
                        icon="ios-search"
                        class="score"
                    >查看成绩</i-button>
                </Col>
            </Row>

            <Row>
                <Col span="7">
                    <!-- 政策解读是page2 -->
                    <i-button
                        id="bt2"
                        @click="toPolicy"
                        type="primary"
                        icon="android-document"
                        class="policy"
                    >政策解读</i-button>
                </Col>
                <Col span="7">
                    <!-- 名校直通车是page3 -->
                    <i-button @click="toEliteSchool" type="primary" icon="key" class="direct">名校直通车</i-button>
                </Col>
                <Col span="10">
                    <i-button
                        @click="toEnrollmentGuide"
                        icon="document-text"
                        type="primary"
                        class="regulation"
                    >招生简章</i-button>
                </Col>
            </Row>

            <Row>
                <Col span="10">
                    <i-button
                        @click="toProfessionTest"
                        icon="ios-paw"
                        type="primary"
                        class="test"
                    >职业测试</i-button>
                </Col>
                <Col span="14">
                    <!-- 专业详解是page8 -->
                    <i-button
                        @click="toMajorExplanation"
                        type="primary"
                        icon="document-text"
                        class="major"
                    >专业详解</i-button>
                </Col>
            </Row>
        </div>

        <Button class="font" type="text" @click="signOut">
            <Icon type="android-arrow-back" size="32" color="#fff"></Icon>退出登录
        </Button>
    </div>
</template>

<script>
import screenfull from "screenfull";
import Cookies from "js-cookie";

export default {
    name: "buttonHome",
    data() {
        return {
            msg: "中心服务自助终端",
            login_modal: false,
            form: {
                userName: "",
                password: ""
            },
            rules: {
                userName: [
                    { required: true, message: "账号不能为空", trigger: "blur" }
                ],
                password: [
                    { required: true, message: "密码不能为空", trigger: "blur" }
                ]
            }
        };
    },
    methods: {
        screenFull() {
            if (!screenfull.enabled) {
                // 如果不允许进入全屏，发出不允许提示
                this.$message({
                    message: "不支持全屏",
                    type: "warning"
                });
                return false;
            }
            screenfull.toggle();
            this.$message({
                message: "全屏啦",
                type: "success"
            });
        },
        loginModal() {
            this.login_modal = true;
        },
        handleSubmit() {
            console.log("LSKDMNOLASKD")
            this.$http({
                method:'post',
                url:"http://118.202.11.253:8085/home/login",
                data:{
                    "userName":this.form.userName,
                    "password":this.form.password
                }
            }).then(resp =>{
                if(resp.data.code==123){
                    this.$Message.error("没有此用户");
                }else if(resp.data.code==124){
                    this.$Message.warning("密码错误请重新输入");
                }else if(resp.data.code==200){
                    this.$Message.success("亲爱的，您已登陆");
                    this.login_modal = false;
                }
                
            }).catch(resp => {
                console.log('请求失败：'+resp.status+','+resp.statusText);
              });
            this.$refs.loginForm.validate(valid => {
                if (valid) {
                    Cookies.set("user", this.form.userName);
                    Cookies.set("password", this.form.password);
                    if (this.form.userName === "iview_admin") {
                        Cookies.set("access", 0);
                    } else {
                        Cookies.set("access", 1);
                    }
            
                }
            });
        },
        signOut() {
            Cookies.remove('userName')
            Cookies.remove('userId')
            this.$Message.info("亲爱的, 您已退出");
        },
        toIndependentRecruitment() {
            this.$router.push({
                //自主招生
                path:
                    "/buttonHome/independentRecruitment/main/independentRecruitmentPolicy"
            });
        },
        toPolicy() {
            this.$router.push({
                //政策解读
                path: "/buttonHome/policy"
            });
        },
        toMajorExplanation() {
            this.$router.push({
                //专业详解
                path: "/buttonHome/majorExplanation"
            });
        },
        toEnrollmentGuide() {
            this.$router.push({
                //招生简章
                path: "/buttonHome/enrollmentGuide"
            });
        },
        toEliteSchool() {
            this.$router.push({
                //名校直通车
                path: "/buttonHome/eliteSchool"
            });
        },
        toVoluntaryReporting() {
            this.$router.push({
                //志愿填报查询
                path: "/buttonHome/voluntaryReporting"
            });
        },
        toProfessionTest() {
            this.$router.push({
                //职业测试
                path: "/buttonHome/professionTest"
            });
        },
        toCheckScores() {
            this.$router.push({
                //查看成绩
                path: "/buttonHome/checkScores"
            });
        }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.screenfull-button {
    opacity: 0;
}
.login-bt {
    background-color: #ff9999;
}
.login-tip {
    font-size: 0.625rem;
    text-align: center;
    color: #c3c3c3;
}
.font {
    color: #f0f8ff;
}
.allButtons {
    padding: 2rem;
    padding-left: 5rem;
    padding-right: 5rem;
    text-align: center;
    margin: 0 auto;
}
.students {
    font-size: 250%;
    border-radius: 0.618rem;
    width: 28.7rem;
    height: 10rem;
    border: none;
    background-color: rgb(99, 146, 235);
    color: #f0f8ff;
}
.voluntary {
    background-color: rgb(51, 218, 162);
    border-radius: 0.618rem;
    width: 35rem;
    height: 10rem;
    font-size: 250%;
    color: #f0f8ff;
}
.score {
    font-size: 250%;
    width: 13rem;
    height: 10rem;
    border-radius: 0.618rem;
    background-color: #4d438a;
    color: #f0f8ff;
}
.policy {
    font-size: 250%;
    width: 22.4rem;
    height: 15rem;
    border-radius: 0.618rem;
    background-color: #2e2c2c;
    color: #f0f8ff;
}
.direct {
    font-size: 250%;
    width: 22.2rem;
    height: 15rem;
    border-radius: 0.618rem;
    background-color: rgb(241, 123, 123);
    color: #f0f8ff;
}
.regulation {
    font-size: 250%;
    width: 32rem;
    height: 15rem;
    border-radius: 0.618rem;
    background-color: #f0622f;
    color: #f0f8ff;
}
.test {
    font-size: 250%;
    width: 31.8rem;
    height: 12.5rem;
    border-radius: 0.618rem;
    background-color: rgb(247, 139, 193);
    color: #f0f8ff;
}
.major {
    font-size: 250%;
    width: 44.6rem;
    height: 12.5rem;
    border-radius: 0.618rem;
    background-color: #2d2d8b;
    color: #f0f8ff;
}
.shadow {
    box-shadow: 0.0625rem 0.4375rem 1.5625rem #fd8fd9;
}
</style>
