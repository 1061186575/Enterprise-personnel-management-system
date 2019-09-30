<template>
  <div class="edit container">

    <h1 class="page-header">编辑员工</h1>
    <router-link to="/" class="layui-btn layui-btn-sm"><i class="layui-icon"></i>&nbsp;返回</router-link>
    <br> <br>
    <form v-on:submit="updateCustomer">
    	<div class="well">
    		<h4>员工信息</h4>
        <div class="form-group">
    			<label>ID</label>
    			<input type="text" class="form-control" placeholder="id" v-model="customer.myid">
    		</div>

        <div class="form-group">
    			<label>姓名</label>
    			<input type="text" class="form-control" placeholder="name" v-model="customer.name">
    		</div>

        <div class="form-group">
          <div>性别</div>
          <select v-model="customer.sex" style="width: 200px;height: 30px;">
            <option value=""></option>
            <option value="男">男</option>
            <option value="女">女</option>
          </select>
        </div>


    		<div class="form-group">
    			<label>电话</label>
    			<input type="text" class="form-control" placeholder="phone" v-model="customer.phone">
    		</div>
    		<div class="form-group">
    			<label>邮箱</label>
    			<input type="text" class="form-control" placeholder="email" v-model="customer.email">
    		</div>


    		<div class="form-group">
    			<label>学历</label>
    			<input type="text" class="form-control" placeholder="education" v-model="customer.education">
    		</div>
    		<div class="form-group">
    			<label>毕业学校</label>
    			<input type="text" class="form-control" placeholder="graduationschool" v-model="customer.graduationschool">
    		</div>
    		<div class="form-group">
    			<label>职务</label>
    			<input type="text" class="form-control" placeholder="profession" v-model="customer.profession">
    		</div>

        <div class="form-group">
    			<label>月薪</label>
    			<input type="text" class="form-control" placeholder="salary" v-model="customer.salary">
    		</div>

        <div class="form-group">
    			<label>现住址</label>
    			<input type="text" class="form-control" placeholder="address" v-model="customer.address">
    		</div>
        <div class="form-group">
    			<label>入职日期</label>
    			<input type="text" class="form-control" placeholder="data" v-model="customer.data">
    		</div>
        <div class="form-group">
    			<label>身份证号码</label>
    			<input type="text" class="form-control" placeholder="card" v-model="customer.card">
    		</div>

    		<div class="form-group">
    			<label>个人简介</label>
    			<!-- <input type="text" class="form-control" placeholder="profile" v-model="customer.profile"> -->
    			<textarea class="form-control" rows="10" v-model="customer.profile"></textarea>
    		</div>
    		<button type="submit" class="btn btn-primary">确认</button>
    	</div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'add',
  data () {
    return {
      customer:{},
    }
  },
  methods:{
    fetchCustomer(id){
        this.$http.get("http://localhost:3000/users/"+id)
            .then(function(response){
              // console.log(response);
              this.customer = response.body;
            })
    },
  	updateCustomer(e){
		e.preventDefault();
  		if (!this.customer.myid||!this.customer.name || !this.customer.sex || !this.customer.phone) {
            layui.use('layer', function(){
                  var layer = layui.layer;
                  layer.msg('ID、姓名、性别、电话为必填选项!');
                });
  		}else{
  			let updateCustomer = {
					myid:this.customer.myid,
					name:this.customer.name,
					sex:this.customer.sex,
					phone:this.customer.phone,
					email:this.customer.email,
					education:this.customer.education,
					graduationschool:this.customer.graduationschool,
					profession:this.customer.profession,
					salary:this.customer.salary,
					address:this.customer.address,
					data:this.customer.data,
					card:this.customer.card,
					profile:this.customer.profile
  			}
  			this.$http.put("http://localhost:3000/users/"+this.$route.params.id,updateCustomer)
  				.then(function(response){
  					// console.log(response);
                    layui.use('layer', function(){
                          var layer = layui.layer;
                          layer.msg('用户信息更新成功!');
                        });
  					this.$router.push({path:"/"});
  			})
  		}
  	}
  },
  created(){
    this.fetchCustomer(this.$route.params.id);
  },
  components:{

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
