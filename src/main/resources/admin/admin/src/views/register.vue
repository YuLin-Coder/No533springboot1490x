<template>
	<div>
		<div class="container" :style='{"minHeight":"100vh","alignItems":"center","background":"url(http://codegen.caihongy.cn/20220722/898b4b26c0464f8caa1cd58e5eafe0c9.png)","display":"flex","width":"100%","backgroundSize":"cover","backgroundPosition":"center center","backgroundRepeat":"no-repeat","justifyContent":"center"}'>
			<el-form v-if="pageFlag=='security1'" :style='{"border":" 8px solid #FFFFFF","padding":"30px 20px","margin":"0","borderRadius":"0 0 50px 50px","top":"0","background":"rgba(228, 239, 254, 0.8000)","width":"450px","position":"absolute","height":"auto"}' ref="rgsForm" class="rgs-form" :model="rgsForm">
				<div v-if="true" :style='{"padding":"10px 20px","margin":"0 0 20px 0","color":"#000","textAlign":"center","width":"100%","lineHeight":"44px","fontSize":"24px","height":"auto"}' class="title">基于文学创作的社交论坛找回密码</div>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">账号</div>
					<el-input v-model="ruleForm.username" autocomplete="off" placeholder="请您输入账号" />
				</el-form-item>
				<button :style='{"border":"0","cursor":"pointer","padding":"0 10px","boxShadow":"0px 4px 10px 0px rgba(0,0,0,0.3020)","margin":"20px auto 15px","color":"#fff","display":"block","outline":"none","borderRadius":"8px","background":"rgba(126, 169, 228, 1)","width":"80%","fontSize":"16px","height":"44px"}' type="button" class="r-btn" @click="getSecurity()">下一步</button>
				<div :style='{"cursor":"pointer","padding":"0 10%","color":"rgba(159, 159, 159, 1)","textAlign":"center","display":"inline-block","width":"100%","lineHeight":"1","fontSize":"12px","textDecoration":"underline"}' class="r-login" @click="close()">已有账号，直接登录</div>
            </el-form>
			<el-form v-if="pageFlag=='security2'" :style='{"border":" 8px solid #FFFFFF","padding":"30px 20px","margin":"0","borderRadius":"0 0 50px 50px","top":"0","background":"rgba(228, 239, 254, 0.8000)","width":"450px","position":"absolute","height":"auto"}' ref="rgsForm" class="rgs-form" :model="rgsForm">
				<div v-if="true" :style='{"padding":"10px 20px","margin":"0 0 20px 0","color":"#000","textAlign":"center","width":"100%","lineHeight":"44px","fontSize":"24px","height":"auto"}' class="title">基于文学创作的社交论坛密码重置</div>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">密保问题</div>
					<el-input v-model="ruleForm.pquestion" readOnly autocomplete="off" placeholder="密保问题" />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">密保答案</div>
					<el-input v-model="ruleForm.myanswer" autocomplete="off" placeholder="请您输入密保答案" />
				</el-form-item>
				<button :style='{"border":"0","cursor":"pointer","padding":"0 10px","boxShadow":"0px 4px 10px 0px rgba(0,0,0,0.3020)","margin":"20px auto 15px","color":"#fff","display":"block","outline":"none","borderRadius":"8px","background":"rgba(126, 169, 228, 1)","width":"80%","fontSize":"16px","height":"44px"}' type="button" class="r-btn" @click="validateSecurity()">下一步</button>
				<div :style='{"cursor":"pointer","padding":"0 10%","color":"rgba(159, 159, 159, 1)","textAlign":"center","display":"inline-block","width":"100%","lineHeight":"1","fontSize":"12px","textDecoration":"underline"}' class="r-login" @click="close()">已有账号，直接登录</div>
            </el-form>
			<el-form v-if="pageFlag=='security3'" :style='{"border":" 8px solid #FFFFFF","padding":"30px 20px","margin":"0","borderRadius":"0 0 50px 50px","top":"0","background":"rgba(228, 239, 254, 0.8000)","width":"450px","position":"absolute","height":"auto"}' ref="rgsForm" class="rgs-form" :model="rgsForm">
				<div v-if="true" :style='{"padding":"10px 20px","margin":"0 0 20px 0","color":"#000","textAlign":"center","width":"100%","lineHeight":"44px","fontSize":"24px","height":"auto"}' class="title">基于文学创作的社交论坛密码重置</div>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">新密码</div>
					<el-input v-model="ruleForm.newpassword" autocomplete="off" type="password" placeholder="请您输入新密码" />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">确认密码</div>
					<el-input v-model="ruleForm.repassword" autocomplete="off" type="password" placeholder="请您确认新密码" />
				</el-form-item>
				<button :style='{"border":"0","cursor":"pointer","padding":"0 10px","boxShadow":"0px 4px 10px 0px rgba(0,0,0,0.3020)","margin":"20px auto 15px","color":"#fff","display":"block","outline":"none","borderRadius":"8px","background":"rgba(126, 169, 228, 1)","width":"80%","fontSize":"16px","height":"44px"}' type="button" class="r-btn" @click="updatePassword()">修改密码</button>
				<div :style='{"cursor":"pointer","padding":"0 10%","color":"rgba(159, 159, 159, 1)","textAlign":"center","display":"inline-block","width":"100%","lineHeight":"1","fontSize":"12px","textDecoration":"underline"}' class="r-login" @click="close()">已有账号，直接登录</div>
            </el-form>
			<el-form v-if="pageFlag=='register'" :style='{"border":" 8px solid #FFFFFF","padding":"30px 20px","margin":"0","borderRadius":"0 0 50px 50px","top":"0","background":"rgba(228, 239, 254, 0.8000)","width":"450px","position":"absolute","height":"auto"}' ref="rgsForm" class="rgs-form" :model="rgsForm">
				<div v-if="true" :style='{"padding":"10px 20px","margin":"0 0 20px 0","color":"#000","textAlign":"center","width":"100%","lineHeight":"44px","fontSize":"24px","height":"auto"}' class="title">基于文学创作的社交论坛注册</div>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item" v-if="tableName=='yonghu'">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">用户账号</div>
					<el-input  v-model="ruleForm.yonghuzhanghao"  autocomplete="off" placeholder="用户账号"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item" v-if="tableName=='yonghu'">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">密码</div>
					<el-input  v-model="ruleForm.mima"  autocomplete="off" placeholder="密码"  type="password"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item" v-if="tableName=='yonghu'">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">确认密码</div>
					<el-input  v-model="ruleForm.mima2" autocomplete="off" placeholder="确认密码" type="password" />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item" v-if="tableName=='yonghu'">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">用户姓名</div>
					<el-input  v-model="ruleForm.yonghuxingming"  autocomplete="off" placeholder="用户姓名"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item" v-if="tableName=='yonghu'">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">性别</div>
                    <el-select v-model="ruleForm.xingbie" placeholder="请选择性别" >
                        <el-option
                            v-for="(item,index) in yonghuxingbieOptions"
                            v-bind:key="index"
                            :label="item"
                            :value="item">
                        </el-option>
                    </el-select>
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item" v-if="tableName=='yonghu'">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">年龄</div>
					<el-input  v-model="ruleForm.nianling"  autocomplete="off" placeholder="年龄"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item" v-if="tableName=='yonghu'">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">头像</div>
                    <file-upload
                        tip="点击上传头像"
                        action="file/upload"
                        :limit="3"
                        :multiple="true"
                        :fileUrls="ruleForm.touxiang?ruleForm.touxiang:''"
                        @change="yonghutouxiangUploadChange"
                    ></file-upload>
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item" v-if="tableName=='yonghu'">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">密保问题</div>
					<el-input  v-model="ruleForm.pquestion"  autocomplete="off" placeholder="密保问题"  type="text"  />
				</el-form-item>
				<el-form-item :style='{"width":"80%","padding":"0","margin":"0 auto 15px","height":"auto"}' class="list-item" v-if="tableName=='yonghu'">
					<div v-if="false" :style='{"width":"64px","lineHeight":"44px","fontSize":"14px","color":"rgba(64, 158, 255, 1)"}' class="lable">密保答案</div>
					<el-input  v-model="ruleForm.panswer"  autocomplete="off" placeholder="密保答案"  type="text"  />
				</el-form-item>
				<button :style='{"border":"0","cursor":"pointer","padding":"0 10px","boxShadow":"0px 4px 10px 0px rgba(0,0,0,0.3020)","margin":"20px auto 15px","color":"#fff","display":"block","outline":"none","borderRadius":"8px","background":"rgba(126, 169, 228, 1)","width":"80%","fontSize":"16px","height":"44px"}' type="button" class="r-btn" @click="login()">注册</button>
				<div :style='{"cursor":"pointer","padding":"0 10%","color":"rgba(159, 159, 159, 1)","textAlign":"center","display":"inline-block","width":"100%","lineHeight":"1","fontSize":"12px","textDecoration":"underline"}' class="r-login" @click="close()">已有账号，直接登录</div>
			</el-form>
			
		</div>
	</div>
</template>

<script>

export default {
	data() {
		return {
			ruleForm: {
                xingbie: '',
			},

            pageFlag : '',
			tableName:"",
			rules: {},
            yonghuxingbieOptions: [],
		};
	},
	mounted(){
        this.pageFlag = this.$storage.get("pageFlag");
		let table = this.$storage.get("loginTable");
		this.tableName = table;
        this.yonghuxingbieOptions = "男,女".split(',')
	},
	created() {
    
	},
	destroyed() {
		  	},
	methods: {
		// 获取uuid
		getUUID () {
			return new Date().getTime();
		},
		close(){
			this.$router.push({ path: "/login" });
		},
        yonghutouxiangUploadChange(fileUrls) {
            this.ruleForm.touxiang = fileUrls;
        },

        // 多级联动参数


        //获取密保问题
        getSecurity(){
            this.tableName = 'yonghu'
            if(!this.tableName) {
                this.$message.error("请选择角色");
                return false
            }
            if(!this.ruleForm.username){
                this.$message.error("请输入账号");
                return false
            }
            this.$http({
                url: this.tableName+`/security?username=` + this.ruleForm.username,
                method: "get",
            }).then(({
                data
            }) => {
                if (data.data && data.code === 0) {
                    this.ruleForm = data.data;
                    this.pageFlag="security2"
                } else {
                    if(!data.data) {
                        this.$message.error("用户不存在");
                    } else {
                        this.$message.error(data.msg);
                    }
                }
            });
        },
        //验证密保问题
        validateSecurity(){
            let that = this
            if(this.ruleForm.panswer!=this.ruleForm.myanswer){
                this.$message.error("答案输入不正确");
                return false
            }
            this.$message.success("答案正确");
            setTimeout(()=>{
                this.pageFlag="security3";
            },1000)
            
        },
        // 修改密码
        updatePassword() {
            if (this.ruleForm.newpassword != this.ruleForm.repassword) {
                this.$message.error("两次密码输入不一致");
                return;
            }
            this.ruleForm.mima = this.ruleForm.newpassword;
            this.ruleForm.password = this.ruleForm.newpassword;
            this.$http({
                url: this.tableName+`/update`,
                method: "post",
                data: this.ruleForm
            }).then(({
                data
            }) => {
                if (data && data.code === 0) {
                    this.$message({
                        message: "修改密码成功",
                        type: "success",
                        duration: 1500,
                        onClose: () => {}
                    });
                    this.close()
                } else {
                    this.$message.error(data.msg);
                }
            });
        },
		// 注册
		login() {
			var url=this.tableName+"/register";
					if((!this.ruleForm.yonghuzhanghao) && `yonghu` == this.tableName){
						this.$message.error(`用户账号不能为空`);
						return
					}
					
					
					
					
					
					
					
					
					
					
					if((!this.ruleForm.mima) && `yonghu` == this.tableName){
						this.$message.error(`密码不能为空`);
						return
					}
					
					
					
					
					
					
					
					
					
					
					if((this.ruleForm.mima!=this.ruleForm.mima2) && `yonghu` == this.tableName){
						this.$message.error(`两次密码输入不一致`);
						return
					}
					if((!this.ruleForm.yonghuxingming) && `yonghu` == this.tableName){
						this.$message.error(`用户姓名不能为空`);
						return
					}
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					if(`yonghu` == this.tableName && this.ruleForm.nianling&&(!this.$validate.isIntNumer(this.ruleForm.nianling))){
						this.$message.error(`年龄应输入整数`);
						return
					}
					
					
					
					
					
					
					
            if(this.ruleForm.touxiang!=null) {
                this.ruleForm.touxiang = this.ruleForm.touxiang.replace(new RegExp(this.$base.url,"g"),"");
            }
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
					
				
			
			this.$http({
				url: url,
				method: "post",
				data:this.ruleForm
			}).then(({ data }) => {
				if (data && data.code === 0) {
					this.$message({
						message: "注册成功",
						type: "success",
						duration: 1500,
						onClose: () => {
							this.$router.replace({ path: "/login" });
						}
					});
				} else {
					this.$message.error(data.msg);
				}
			});
		}
	}
};
</script>

<style lang="scss" scoped>
	.container {
	  position: relative;
	  background: url(http://codegen.caihongy.cn/20220722/898b4b26c0464f8caa1cd58e5eafe0c9.png);

		.el-date-editor.el-input {
		  width: 100%;
		}
		
		.rgs-form .el-input /deep/ .el-input__inner {
						border: 0;
						border-radius: 8px;
						padding: 0 10px;
						box-shadow: 0px 4px 10px 0px rgba(0,0,0,0.3020);
						outline: none;
						color: #333;
						width: 100%;
						font-size: 14px;
						height: 44px;
					}
		
		.rgs-form .el-select /deep/ .el-input__inner {
						border: 0;
						border-radius: 8px;
						padding: 0 10px;
						box-shadow: 0px 4px 10px 0px rgba(0,0,0,0.3020);
						outline: none;
						color: #333;
						width: 315px;
						font-size: 14px;
						height: 44px;
					}
		
		.rgs-form .el-date-editor /deep/ .el-input__inner {
						border: 0;
						border-radius: 8px;
						padding: 0 10px 0 30px;
						box-shadow: 0px 4px 10px 0px rgba(0,0,0,0.3020);
						outline: none;
						color: #333;
						width: 100%;
						font-size: 14px;
						height: 44px;
					}
		
		.rgs-form .el-date-editor /deep/ .el-input__inner {
						border: 0;
						border-radius: 8px;
						padding: 0 10px 0 30px;
						box-shadow: 0px 4px 10px 0px rgba(0,0,0,0.3020);
						outline: none;
						color: #333;
						width: 100%;
						font-size: 14px;
						height: 44px;
					}
		
		.rgs-form /deep/ .el-upload--picture-card {
			background: transparent;
			border: 0;
			border-radius: 0;
			width: auto;
			height: auto;
			line-height: initial;
			vertical-align: middle;
		}
		
		.rgs-form /deep/ .upload .upload-img {
		  		  border: 1px dashed rgba(0,0,0,0.3020);
		  		  cursor: pointer;
		  		  border-radius: 8px;
		  		  color: #333;
		  		  background: #fff;
		  		  width: 100px;
		  		  font-size: 32px;
		  		  line-height: 100px;
		  		  text-align: center;
		  		  height: 100px;
		  		}
		
		.rgs-form /deep/ .el-upload-list .el-upload-list__item {
		  		  border: 1px dashed rgba(0,0,0,0.3020);
		  		  cursor: pointer;
		  		  border-radius: 8px;
		  		  color: #333;
		  		  background: #fff;
		  		  width: 100px;
		  		  font-size: 32px;
		  		  line-height: 100px;
		  		  text-align: center;
		  		  height: 100px;
		  		}
		
		.rgs-form /deep/ .el-upload .el-icon-plus {
		  		  border: 1px dashed rgba(0,0,0,0.3020);
		  		  cursor: pointer;
		  		  border-radius: 8px;
		  		  color: #333;
		  		  background: #fff;
		  		  width: 100px;
		  		  font-size: 32px;
		  		  line-height: 100px;
		  		  text-align: center;
		  		  height: 100px;
		  		}
	}
</style>
